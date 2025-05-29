```
sig = signature(sigsv::SimpleVector)
```

Compute a method signature from a suitable `SimpleVector`: `sigsv[1]` holds the signature and `sigsv[2]` the `TypeVar`s.

# Example:

For `f(x::AbstractArray{T}) where T`, the corresponding `sigsv` is constructed as

```
T = TypeVar(:T)
sig1 = Core.svec(typeof(f), AbstractArray{T})
sig2 = Core.svec(T)
sigsv = Core.svec(sig1, sig2)
sig = signature(sigsv)
```
