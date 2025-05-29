```
aws_event_stream_channel_handler_new(allocator, handler_options)
```

Allocates and initializes a new channel handler for processing [`aws_event_stream_message`](@ref)() events. Handler options must not be null.

### Prototype

```c
struct aws_channel_handler *aws_event_stream_channel_handler_new( struct aws_allocator *allocator, const struct aws_event_stream_channel_handler_options *handler_options);
```
