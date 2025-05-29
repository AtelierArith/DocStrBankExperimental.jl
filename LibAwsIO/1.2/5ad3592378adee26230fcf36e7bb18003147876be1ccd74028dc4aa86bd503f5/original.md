```
aws_event_loop_current_clock_time(event_loop, time_nanos)
```

Gets the current timestamp for the event loop's clock, in nanoseconds. This function is thread-safe.

### Prototype

```c
int aws_event_loop_current_clock_time(const struct aws_event_loop *event_loop, uint64_t *time_nanos);
```
