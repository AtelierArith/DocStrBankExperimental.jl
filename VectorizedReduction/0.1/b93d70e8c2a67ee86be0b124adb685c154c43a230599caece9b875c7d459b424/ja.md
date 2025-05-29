```
vtmapreducethen(f, op, g, init, As::Tuple{Vararg{AbstractArray}}, dims=:)
```

`mapreducethen` の `f` のバージョン : ℝᴺ → ℝ、次に `g` : ℝ → ℝ、指定された `dims` に対しての縮小を行います。
