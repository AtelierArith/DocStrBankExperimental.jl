```
aws_http2_stream_manager_acquire(manager)
```

Acquire a refcount from the stream manager, stream manager will start to destroy after the refcount drops to zero. NULL is acceptable. Initial refcount after new is 1.

# Arguments

  * `manager`:

# Returns

The same pointer acquiring.

### Prototype

```c
struct aws_http2_stream_manager *aws_http2_stream_manager_acquire(struct aws_http2_stream_manager *manager);
```
