---

title: "Installation & Setup"
date: 2019-02-05T18:12:27+01:00
markup: rst
weight: 3

---
====================
Installation & Setup
====================

**Disclaimer**: *Radicle is alpha technology and in heavy development. All your data may be lost. We do not guarantee backwards compatibility between releases. It’s important to remember that this is experimental software and should be treated as such.*

*This release is aimed for developers and early-adopters who want to get a glimpse into what we are building and help shape the product through feedback or contributions to the Radicle project.*

OS X
====


.. code-block::

   brew tap radicle-dev/radicle
   brew install radicle-alpha


To run the ``rad`` commands, you must have both a Radicle daemon, and Radicle IPFS daemon running. You can have them always run in the background using `brew services <https://github.com/Homebrew/homebrew-services>`_
with the following commands:

.. code-block::

   brew services start radicle-alpha-ipfs
   brew services start radicle-alpha


Or if you prefer running them manually every time, check the `section below <#manually-running-background-processes>`_.

Finally, interacting with the Radicle utilities requires that you have a set of Radicle keys. You
can initialize your keys with the ``rad key create`` command.


Debian/Ubuntu
=============

For Debian-based systems we provide packages.

.. code-block::

    wget https://storage.googleapis.com/static.radicle.xyz/releases/radicle_latest_amd64.deb
    sudo apt install ./radicle_latest_amd64.deb

To run the ``rad`` commands, you must have both a Radicle daemon, and Radicle IPFS daemon running. The package includes systemd service files to always have the daemons running in the background. To start the daemons run:

.. code-block::

    systemctl --user start radicle-daemon

You can check the status of a service with ``systemctl --user status <service>``.

Or if you prefer running them manually every time, check the `section below <#manually-running-background-processes>`_.

Finally, interacting with the Radicle utilities requires that you have a set of Radicle keys. You
can initialize your keys with the ``rad key create`` command.


Install From Source
===================

Radicle requires `ipfs`_ and `git-remote-ipfs`_ to run properly. When
installing Radicle from source, make sure you have both of these installed first.

To build Radicle from source you need to install `stack`_.

.. code-block::

   git clone https://github.com/radicle-dev/radicle.git
   cd radicle

   stack install

Note that `stack` might take as much as 4GB of memory to build Radicle.

Manually running background processes
=====================================

Radicle requires 2 background processes to be running: ``radicle-daemon`` and ``radicle-ipfs-daemon``.

If you have installed Radicle via the brew / debian packages, the necessary background processes
should be already available as systemd or brew services respectively (see above).

To run these manually, you can use the following ``rad`` commands:

.. code-block::

   rad daemon-ipfs
   rad daemon-radicle

Finally, interacting with the Radicle utilities requires that you have a set of Radicle keys. You
can initialize your keys with the ``rad key create`` command.

.. _stack: https://docs.haskellstack.org/en/latest/install_and_upgrade/
.. _ipfs: https://docs.ipfs.io/introduction/install/
.. _git-remote-ipfs: https://github.com/oscoin/ipfs/tree/master/git-remote-ipfs#install
