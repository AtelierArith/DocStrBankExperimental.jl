```
isoption(::Const{Nothing}) = true
isoption(::Identity) = true
isoption(other) = false
```

check whether something is a [`Try`](@ref)
