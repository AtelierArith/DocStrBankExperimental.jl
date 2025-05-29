```
isoption(::Const{Nothing}) = true
isoption(::Identity) = true
isoption(other) = false
```

check whether something is an [`Option`](@ref)
