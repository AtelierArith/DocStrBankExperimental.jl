```
aws_http2_stream_manager_release(manager)
```

Release a refcount from the stream manager, stream manager will start to destroy after the refcount drops to zero. NULL is acceptable. Initial refcount after new is 1.

# Arguments

  * `manager`:

# Returns

NULL

### Prototype

```c
struct aws_http2_stream_manager *aws_http2_stream_manager_release(struct aws_http2_stream_manager *manager);
```
