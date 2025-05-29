```
aws_channel_schedule_task_now_serialized(channel, task)
```

Schedules a task to run on the event loop as soon as possible.

This variant always uses the cross thread queue rather than conditionally skipping it when already in the destination event loop. While not "optimal", this allows us to serialize task execution no matter where the task was submitted from: if you are submitting tasks from a critical section, the serialized order that you submit is guaranteed to be the order that they execute on the event loop.

The task should not be cleaned up or modified until its function is executed.

### Prototype

```c
void aws_channel_schedule_task_now_serialized(struct aws_channel *channel, struct aws_channel_task *task);
```
