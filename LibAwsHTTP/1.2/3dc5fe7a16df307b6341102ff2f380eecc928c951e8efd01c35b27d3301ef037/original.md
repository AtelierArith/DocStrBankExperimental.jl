```
aws_http_proxy_config_new_clone(allocator, proxy_config)
```

Clones an existing proxy configuration. A refactor could remove this (do a "move" between the old and new user data in the one spot it's used) but that should wait until we have better test cases for the logic where this gets invoked (ntlm/kerberos chains).

# Arguments

  * `allocator`: memory allocator to use
  * `proxy_config`: http proxy configuration to clone

# Returns

### Prototype

```c
struct aws_http_proxy_config *aws_http_proxy_config_new_clone( struct aws_allocator *allocator, const struct aws_http_proxy_config *proxy_config);
```
