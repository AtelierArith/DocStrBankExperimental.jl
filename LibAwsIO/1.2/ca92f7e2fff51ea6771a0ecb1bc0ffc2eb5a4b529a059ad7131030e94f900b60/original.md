```
aws_event_loop_schedule_task_future(event_loop, task, run_at_nanos)
```

The event loop will schedule the task and run it at the specified time. Use [`aws_event_loop_current_clock_time`](@ref)() to query the current time in nanoseconds. Note that cancelled tasks may execute outside the event loop thread. This function may be called from outside or inside the event loop thread.

The task should not be cleaned up or modified until its function is executed.

### Prototype

```c
void aws_event_loop_schedule_task_future( struct aws_event_loop *event_loop, struct aws_task *task, uint64_t run_at_nanos);
```
