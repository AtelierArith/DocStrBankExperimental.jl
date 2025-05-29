```
aws_channel_thread_is_callers_thread(channel)
```

Returns true if the caller is on the event loop's thread. If false, you likely need to use aws_channel_schedule_task(). This function is safe to call from any thread.

### Prototype

```c
bool aws_channel_thread_is_callers_thread(struct aws_channel *channel);
```
