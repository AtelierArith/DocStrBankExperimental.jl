```
aws_channel_task_init(channel_task, task_fn, arg, type_tag)
```

Initializes channel_task for use.

### Prototype

```c
void aws_channel_task_init( struct aws_channel_task *channel_task, aws_channel_task_fn *task_fn, void *arg, const char *type_tag);
```
