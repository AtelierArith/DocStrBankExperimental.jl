```
aws_s3express_credentials_provider_init_base(provider, allocator, vtable, impl)
```

To initialize the provider with basic vtable and refcount. And hook up the refcount with vtable functions.

# Arguments

  * `provider`:
  * `allocator`:
  * `vtable`:
  * `impl`: Optional, the impl for the provider

# Returns

[`AWS_S3_API`](@ref)

### Prototype

```c
void aws_s3express_credentials_provider_init_base( struct aws_s3express_credentials_provider *provider, struct aws_allocator *allocator, struct aws_s3express_credentials_provider_vtable *vtable, void *impl);
```
