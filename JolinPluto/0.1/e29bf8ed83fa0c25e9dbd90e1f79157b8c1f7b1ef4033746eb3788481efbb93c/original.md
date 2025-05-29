```
ChannelWithRepeatedFill(get_next_value, 2; sleep_seconds=1.0)
```

Creates a ChannelPluto which calls `get_next_value` repeatedly, interleaved by calls to sleep of the given time (defaults to 0 seconds sleep).
