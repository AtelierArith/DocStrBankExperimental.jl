```
aws_secure_tunnel_release(secure_tunnel)
```

Release a reference to a secure tunnel. When the secure tunnel ref count drops to zero, the secure tunnel will automatically trigger a stop and once the stop completes, the secure tunnel will delete itself.

# Arguments

  * `secure_tunnel`: secure tunnel to release a reference to. May be NULL

# Returns

NULL

### Prototype

```c
struct aws_secure_tunnel *aws_secure_tunnel_release(struct aws_secure_tunnel *secure_tunnel);
```
