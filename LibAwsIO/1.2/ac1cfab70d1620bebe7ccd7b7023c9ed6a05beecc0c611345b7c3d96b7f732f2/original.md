```
aws_pkcs11_lib_release(pkcs11_lib)
```

Release a reference to the PKCS#11 library. When the last reference is released, the library is cleaned up.

### Prototype

```c
void aws_pkcs11_lib_release(struct aws_pkcs11_lib *pkcs11_lib);
```
