```
aws_event_loop_group_new_default(alloc, max_threads, shutdown_options)
```

!!! compat "非推奨"
      * 代わりに [`aws_event_loop_group_new`](@ref)() を使用してください


### プロトタイプ

```c
struct aws_event_loop_group *aws_event_loop_group_new_default( struct aws_allocator *alloc, uint16_t max_threads, const struct aws_shutdown_callback_options *shutdown_options);
```
