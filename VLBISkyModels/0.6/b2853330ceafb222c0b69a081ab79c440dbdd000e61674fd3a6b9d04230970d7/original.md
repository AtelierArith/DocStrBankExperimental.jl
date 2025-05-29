```
getparam(m, s::Symbol, p)
```

Gets the parameter value `s` from the model `m` evaluated at the domain `p`.  This is similar to getproperty, but allows for the parameter to be a function of the  domain. Essentially is `m.s <: DomainParams` then `m.s` is evaluated at the parameter `p`. If `m.s` is not a subtype of `DomainParams` then `m.s` is returned.

!!! warn
    Developers should not typically overload this function and instead target [`build_param`](@ref).


!!! warn
    This feature is experimental and is not considered part of the public stable API.

