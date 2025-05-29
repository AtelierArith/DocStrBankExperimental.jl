```
aws_secure_tunnel_message_type_to_c_string(message_type)
```

Get the const char description of a message type

# Arguments

  * `message_type`: message type used by a secure tunnel message

# Returns

const char translation of the message type

### Prototype

```c
const char *aws_secure_tunnel_message_type_to_c_string(enum aws_secure_tunnel_message_type message_type);
```
