```
aws_secure_tunnel_acquire(secure_tunnel)
```

Acquires a reference to a secure tunnel

# Arguments

  * `secure_tunnel`: secure tunnel to acquire a reference to. May be NULL

# Returns

what was passed in as the secure tunnel (a client or NULL)

### Prototype

```c
struct aws_secure_tunnel *aws_secure_tunnel_acquire(struct aws_secure_tunnel *secure_tunnel);
```
