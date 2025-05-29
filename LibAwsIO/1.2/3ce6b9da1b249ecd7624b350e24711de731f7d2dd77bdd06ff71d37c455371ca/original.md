```
testing_channel_run_currently_queued_tasks(testing)
```

Executes all currently scheduled tasks whose time has come. Use [`testing_channel_drain_queued_tasks`](@ref)() to repeatedly run tasks until only future-tasks remain.

### Prototype

```c
static inline void testing_channel_run_currently_queued_tasks(struct testing_channel *testing);
```
