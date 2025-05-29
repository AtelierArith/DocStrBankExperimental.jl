```
@hash_call f(args; kwargs)
```

Computes the hash of the function call `f(args; kwargs)` by hashing `f`, the values of `args`, the names of `kwargs`, and the values of `kwargs`.

Different order of kwargs will hash differently. Setting the default values of kwargs explicitly will hash differently than using the defaults implicitly. Splatting is not yet supported.
