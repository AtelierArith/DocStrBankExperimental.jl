```
testing_channel_get_read_message_queue(testing)
```

when you want to test the read output of your handler, call this, get the queue and iterate the messages. A downstream handler must have been installed

### Prototype

```c
static inline struct aws_linked_list *testing_channel_get_read_message_queue(struct testing_channel *testing);
```
