```
testing_channel_drain_queued_tasks(testing)
```

Repeatedly executes scheduled tasks until only those in the future remain. This covers the common case where there's a chain reaction of now-tasks scheduling further now-tasks.

### Prototype

```c
static inline void testing_channel_drain_queued_tasks(struct testing_channel *testing);
```
