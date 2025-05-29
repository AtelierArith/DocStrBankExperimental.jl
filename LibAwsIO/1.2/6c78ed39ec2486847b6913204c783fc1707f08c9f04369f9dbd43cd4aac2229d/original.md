```
aws_tls_ctx_pkcs11_options
```

This struct exists as a graceful way to pass many arguments when calling init-with-pkcs11 functions on [`aws_tls_ctx_options`](@ref) (this also makes it easy to introduce optional arguments in the future). Instances of this struct should only exist briefly on the stack.

Instructions for binding this to high-level languages: - Python: The members of this struct should be the keyword args to the init-with-pkcs11 functions. - JavaScript: This should be an options map passed to init-with-pkcs11 functions. - Java: This should be an options class passed to init-with-pkcs11 functions. - C++: Same as Java

Notes on integer types: PKCS#11 uses `unsigned long` for IDs, handles, etc but we expose them as `uint64_t` in public APIs. We do this because sizeof(long) is inconsistent across platform/arch/language (ex: always 64bit in Java, always 32bit in C on Windows, matches CPU in C on Linux and Apple). By using uint64_t in our public API, we can keep the careful bounds-checking all in one place, instead of expecting each high-level language binding to get it just right.
