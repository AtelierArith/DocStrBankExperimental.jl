```
aws_event_loop_cancel_task(event_loop, task)
```

Cancels task. This function must be called from the event loop's thread, and is only guaranteed to work properly on tasks scheduled from within the event loop's thread. The task will be executed with the AWS_TASK_STATUS_CANCELED status inside this call.

### Prototype

```c
void aws_event_loop_cancel_task(struct aws_event_loop *event_loop, struct aws_task *task);
```
