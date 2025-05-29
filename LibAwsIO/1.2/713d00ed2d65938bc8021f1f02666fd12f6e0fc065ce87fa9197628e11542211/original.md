```
aws_event_loop_schedule_task_now(event_loop, task)
```

The event loop will schedule the task and run it on the event loop thread as soon as possible. Note that cancelled tasks may execute outside the event loop thread. This function may be called from outside or inside the event loop thread.

The task should not be cleaned up or modified until its function is executed.

### Prototype

```c
void aws_event_loop_schedule_task_now(struct aws_event_loop *event_loop, struct aws_task *task);
```
