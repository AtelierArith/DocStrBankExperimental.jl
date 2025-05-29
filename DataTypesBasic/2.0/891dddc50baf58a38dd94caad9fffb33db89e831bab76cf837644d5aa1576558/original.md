```
iseither(::Const) = true
iseither(::Identity) = true
iseither(other) = false
```

check whether something is an [`Either`](@ref)
