```
aws_event_stream_library_clean_up()
```

Clean up internal datastructures used by aws-c-event-stream. Must not be called until application is done using functionality in aws-c-event-stream.

### Prototype

```c
void aws_event_stream_library_clean_up(void);
```
