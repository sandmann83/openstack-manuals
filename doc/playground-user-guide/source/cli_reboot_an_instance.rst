==================
Reboot an instance
==================

You can soft or hard reboot a running instance. A soft reboot attempts a
graceful shut down and restart of the instance. A hard reboot power
cycles the instance.

By default, when you reboot an instance, it is a soft reboot.

.. code::

  $ nova reboot SERVER

To perform a hard reboot, pass the ``--hard`` parameter, as follows:

.. code::

  $ nova reboot --hard SERVER

It is also possible to reboot a running instance into rescue mode. For example,
this operation may be required, if a filesystem of an instance becomes
corrupted with prolonged use.

.. note::

  Pause, suspend, and stop operations are not allowed when an instance
  is running in rescue mode, as triggering these actions causes the
  loss of the original instance state, and makes it impossible to
  unrescue the instance.

Rescue mode provides a mechanism for access, even if an image renders
the instance inaccessible. By default, it starts an instance from the
initial image attaching the current boot disk as a secondary one.

To perform an instance reboot into rescue mode, run the following
command:

.. code::

  $ nova rescue SERVER

To restart the instance from the normal boot disk, run the following
command:

.. code::

  $ nova unrescue SERVER

If you want to rescue an instance with a specific image, rather than the
default one, use the ``--rescue_image_ref`` parameter:

.. code::

  $ nova rescue --rescue_image_ref IMAGE_ID SERVER
