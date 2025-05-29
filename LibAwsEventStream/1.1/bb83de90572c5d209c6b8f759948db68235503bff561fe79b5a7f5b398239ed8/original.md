```
aws_event_stream_library_init(allocator)
```

Initializes internal datastructures used by aws-c-event-stream. Must be called before using any functionality in aws-c-event-stream.

### Prototype

```c
void aws_event_stream_library_init(struct aws_allocator *allocator);
```
