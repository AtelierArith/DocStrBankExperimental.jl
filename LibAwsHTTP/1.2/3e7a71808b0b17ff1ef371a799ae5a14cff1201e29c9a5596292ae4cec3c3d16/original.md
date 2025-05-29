```
aws_http_message_get_headers(message)
```

This datastructure has more functions for inspecting and modifying headers than are available on the [`aws_http_message`](@ref) datastructure.

### Prototype

```c
struct aws_http_headers *aws_http_message_get_headers(const struct aws_http_message *message);
```
