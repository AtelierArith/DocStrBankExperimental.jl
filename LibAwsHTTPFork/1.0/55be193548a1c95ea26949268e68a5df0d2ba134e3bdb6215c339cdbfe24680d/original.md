```
aws_http_stream_release(stream)
```

Users must release the stream when they are done with it, or its memory will never be cleaned up. This will not cancel the stream, its callbacks will still fire if the stream is still in progress.

Tips for language bindings: - Invoke this from the wrapper class's finalizer/destructor. - Do not let the wrapper class be destroyed until on_complete() has fired.

### Prototype

```c
void aws_http_stream_release(struct aws_http_stream *stream);
```
