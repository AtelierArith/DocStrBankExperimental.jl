```
vtmapreducethen(f, op, g, init, As::Vararg{AbstractArray, N}) where {N}
```

Version of `mapreducethen` for `f` : ℝᴺ → ℝ, then `g` : ℝ → ℝ, with reduction occurring over all dimensions.
