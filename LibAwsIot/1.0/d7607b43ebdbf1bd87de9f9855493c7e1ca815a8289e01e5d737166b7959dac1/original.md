```
aws_secure_tunnel_new(allocator, options)
```

Creates a new secure tunnel

# Arguments

  * `options`: secure tunnel configuration

# Returns

a new secure tunnel or NULL

### Prototype

```c
struct aws_secure_tunnel *aws_secure_tunnel_new( struct aws_allocator *allocator, const struct aws_secure_tunnel_options *options);
```
