```
vtmapreducethen(f, op, g, init, As::Tuple{Vararg{AbstractArray}}, dims=:)
```

Version of `mapreducethen` for `f` : ℝᴺ → ℝ, then `g` : ℝ → ℝ, with reduction over given `dims`.
