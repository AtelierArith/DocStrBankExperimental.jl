```
aws_http_stream_send_response(stream, response)
```

Send response (only callable from "request handler" streams) The response object must stay alive at least until the stream's on_complete is called.

### Prototype

```c
int aws_http_stream_send_response(struct aws_http_stream *stream, struct aws_http_message *response);
```
