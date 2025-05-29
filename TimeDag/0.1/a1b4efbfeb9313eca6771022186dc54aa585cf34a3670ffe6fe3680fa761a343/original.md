```
wrapb(f::Function; time_agnostic=true)
```

`wrapb` is like [`wrap`](@ref), however `f` will be broadcasted over all input values.
