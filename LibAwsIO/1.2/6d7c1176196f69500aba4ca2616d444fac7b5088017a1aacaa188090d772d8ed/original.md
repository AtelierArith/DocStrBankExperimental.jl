```
aws_pkcs11_lib_acquire(pkcs11_lib)
```

Acquire a reference to a PKCS#11 library, preventing it from being cleaned up. You must call [`aws_pkcs11_lib_release`](@ref)() when you are done with it. This function returns whatever was passed in. It cannot fail.

### Prototype

```c
struct aws_pkcs11_lib *aws_pkcs11_lib_acquire(struct aws_pkcs11_lib *pkcs11_lib);
```
