```
issuccess(::Identity) = true
issuccess(::Const{<:Exception}) = false
```

Similar to [`isright`](@ref), but only defined for `Const{<:Exception}`. Will throw MethodError when applied on other `Const`.
