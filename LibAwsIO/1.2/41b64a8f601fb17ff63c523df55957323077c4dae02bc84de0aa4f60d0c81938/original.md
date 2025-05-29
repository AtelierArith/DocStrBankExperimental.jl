```
aws_default_dns_resolve(allocator, host_name, output_addresses, user_data)
```

WARNING! do not call this function directly (getaddrinfo()): it blocks. Provide a pointer to this function for other resolution functions.

### Prototype

```c
int aws_default_dns_resolve( struct aws_allocator *allocator, const struct aws_string *host_name, struct aws_array_list *output_addresses, void *user_data);
```
