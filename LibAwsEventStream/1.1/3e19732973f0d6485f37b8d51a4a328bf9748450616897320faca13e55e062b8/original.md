```
aws_event_stream_channel_handler_increment_read_window(handler, window_update_size)
```

Updates the read window for the channel if automatic_window_managemanet was set to false.

### Prototype

```c
void aws_event_stream_channel_handler_increment_read_window( struct aws_channel_handler *handler, size_t window_update_size);
```
