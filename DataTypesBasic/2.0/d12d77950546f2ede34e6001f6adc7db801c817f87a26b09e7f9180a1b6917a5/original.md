```
isright(::Const) = false
isright(::Identity) = true
```

Identical to [`isidentity`](@ref), but might be easier to read when working with `Either`.
