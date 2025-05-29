```
aws_channel_schedule_task_future(channel, task, run_at_nanos)
```

Schedules a task to run on the event loop at the specified time. This is the ideal way to move a task into the correct thread. It's also handy for context switches. Use [`aws_channel_current_clock_time`](@ref)() to get the current time in nanoseconds. This function is safe to call from any thread.

The task should not be cleaned up or modified until its function is executed.

### Prototype

```c
void aws_channel_schedule_task_future( struct aws_channel *channel, struct aws_channel_task *task, uint64_t run_at_nanos);
```
