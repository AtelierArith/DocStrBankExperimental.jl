```
testing_channel_complete_written_messages_immediately(testing, complete_immediately, complete_error_code)
```

Set whether written messages have their on_complete callbacks invoked immediately. The on_complete callback will be cleared after it is invoked.

### Prototype

```c
static inline void testing_channel_complete_written_messages_immediately( struct testing_channel *testing, bool complete_immediately, int complete_error_code);
```
