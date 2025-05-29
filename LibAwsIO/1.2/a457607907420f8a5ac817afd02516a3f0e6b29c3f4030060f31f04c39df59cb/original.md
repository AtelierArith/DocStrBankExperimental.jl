```
aws_channel_schedule_task_now(channel, task)
```

Schedules a task to run on the event loop as soon as possible. This is the ideal way to move a task into the correct thread. It's also handy for context switches. This function is safe to call from any thread.

If called from the channel's event loop, the task will get directly added to the run-now list. If called from outside the channel's event loop, the task will go into a cross-thread task queue.

If tasks must be serialized relative to some source synchronization, you may not want to use this API because tasks submitted from the event loop thread can "jump ahead" of tasks submitted from external threads due to this optimization. If this is a problem, you can either refactor your submission logic or use the [`aws_channel_schedule_task_now_serialized`](@ref) variant which does not perform this optimization.

The task should not be cleaned up or modified until its function is executed.

### Prototype

```c
void aws_channel_schedule_task_now(struct aws_channel *channel, struct aws_channel_task *task);
```
