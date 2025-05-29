```
issome(::Identity) = true
issome(::Const{Nothing}) = false
```

Similar to [`isright`](@ref), but only defined for `Const{Nothing}`. Will throw MethodError when applied on other `Const`.
