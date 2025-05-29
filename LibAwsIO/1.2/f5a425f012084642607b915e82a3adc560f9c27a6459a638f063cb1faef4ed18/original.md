```
aws_channel_slot_send_message(slot, message, dir)
```

Sends a message to the adjacent slot in the channel based on dir. Also does window size checking.

NOTE: if this function returns an error code, it is the caller's responsibility to release message back to the pool. If this function returns AWS_OP_SUCCESS, the recipient of the message has taken ownership of the message. So, for example, don't release a message to the pool and then return an error. If you encounter an error condition in this case, shutdown the channel with the appropriate error code.

### Prototype

```c
int aws_channel_slot_send_message( struct aws_channel_slot *slot, struct aws_io_message *message, enum aws_channel_direction dir);
```
