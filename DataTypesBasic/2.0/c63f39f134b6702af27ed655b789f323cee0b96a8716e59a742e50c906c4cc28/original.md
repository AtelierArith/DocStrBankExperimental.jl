```
isnone(::Identity) = false
isnone(::Const{Nothing}) = true
```

Similar to [`isleft`](@ref), but only defined for `Const{Nothing}`. Will throw MethodError when applied on other `Const`.
