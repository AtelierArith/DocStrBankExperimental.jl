```
testing_channel_set_is_on_users_thread(testing, on_users_thread)
```

When you want to force the "not on channel thread path" for your handler, set 'on_users_thread' to false. when you want to undo that, set it back to true. If you set it to false, you'll need to call 'testing_channel_execute_queued_tasks()' to invoke the tasks that ended up being scheduled.

### Prototype

```c
static inline void testing_channel_set_is_on_users_thread(struct testing_channel *testing, bool on_users_thread);
```
