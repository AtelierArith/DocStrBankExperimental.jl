```
isleft(::Const) = true
isleft(::Identity) = false
```

Identical to [`isconst`](@ref), but might be easier to read when working with `Either`.
