```
@unpack_params a,b,c,... = m(p)
```

Extracts the parameters `a,b,c,...` from the model `m` evaluated at the domain `p`. This is a macro that essentially lowers to 

```julia
a = getparam(m, :a, p)
b = getparam(m, :b, p)
...
```

For any model that may depend on a `DomainParams` type this macro should be used to  extract the parameters. 

!!! warn
    This feature is experimental and is not considered part of the public stable API.

