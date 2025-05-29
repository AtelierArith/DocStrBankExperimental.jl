```
aws_channel_current_clock_time(channel, time_nanos)
```

Fetches the current timestamp from the event-loop's clock, in nanoseconds.

### Prototype

```c
int aws_channel_current_clock_time(struct aws_channel *channel, uint64_t *time_nanos);
```
