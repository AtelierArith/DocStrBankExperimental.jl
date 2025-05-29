```
aws_pkcs11_lib_new(allocator, options)
```

Load and initialize a PKCS#11 library. See [`aws_pkcs11_lib_options`](@ref) for options.

If successful a valid pointer is returned. You must call [`aws_pkcs11_lib_release`](@ref)() when you are done with it. If unsuccessful, NULL is returned and an error is set.

### Prototype

```c
struct aws_pkcs11_lib *aws_pkcs11_lib_new( struct aws_allocator *allocator, const struct aws_pkcs11_lib_options *options);
```
