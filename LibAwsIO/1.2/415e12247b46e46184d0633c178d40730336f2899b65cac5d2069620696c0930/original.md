```
aws_event_loop_new_base(allocator, clock, vtable, impl)
```

```c++
 - Don't use outside of testing.

 Initializes the base structure used by all event loop implementations with test-oriented overrides.
 

```

### Prototype

```c
struct aws_event_loop *aws_event_loop_new_base( struct aws_allocator *allocator, aws_io_clock_fn *clock, struct aws_event_loop_vtable *vtable, void *impl);
```
