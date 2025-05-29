```
generative_support_info(method::AbstractDerivativeMethod)::AbstractGenerativeInfo
```

Return the [`AbstractGenerativeInfo`](@ref) associated with `method`. This is intended as an internal method and should be extended for user-defined derivative methods are [`GenerativeDerivativeMethod`](@ref)s.
