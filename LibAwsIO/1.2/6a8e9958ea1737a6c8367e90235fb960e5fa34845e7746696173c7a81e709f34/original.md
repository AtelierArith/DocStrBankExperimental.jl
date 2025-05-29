```
aws_channel_options
```

Args for creating a new channel. event_loop to use for IO and tasks. on_setup_completed will be invoked when the setup process is finished It will be executed in the event loop's thread. on_shutdown_completed will be executed upon channel shutdown.

enable_read_back_pressure toggles whether or not back pressure will be applied in the channel. Leave this option off unless you're using something like reactive-streams, since it is a slight throughput penalty.

Unless otherwise specified all functions for channels and channel slots must be executed within that channel's event-loop's thread.
