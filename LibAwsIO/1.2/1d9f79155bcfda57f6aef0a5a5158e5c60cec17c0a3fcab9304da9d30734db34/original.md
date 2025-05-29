```
aws_event_loop_group_new_default_pinned_to_cpu_group(alloc, max_threads, cpu_group, shutdown_options)
```

!!! compat "Deprecated"
      * use [`aws_event_loop_group_new`](@ref)() instead


### Prototype

```c
struct aws_event_loop_group *aws_event_loop_group_new_default_pinned_to_cpu_group( struct aws_allocator *alloc, uint16_t max_threads, uint16_t cpu_group, const struct aws_shutdown_callback_options *shutdown_options);
```
