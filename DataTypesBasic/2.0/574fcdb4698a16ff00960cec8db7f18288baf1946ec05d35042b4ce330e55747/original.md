```
isfailure(::Identity) = false
isfailure(::Const{<:Exception}) = true
```

Similar to [`isleft`](@ref), but only defined for `Const{<:Exception}`. Will throw MethodError when applied on other `Const`.
