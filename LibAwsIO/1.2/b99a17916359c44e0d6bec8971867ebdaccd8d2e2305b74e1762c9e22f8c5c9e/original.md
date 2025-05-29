```
testing_channel_get_written_message_queue(testing)
```

when you want to test the write output of your handler, call this, get the queue and iterate the messages.

### Prototype

```c
static inline struct aws_linked_list *testing_channel_get_written_message_queue(struct testing_channel *testing);
```
