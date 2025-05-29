```
vtmapreducethen(f, op, g, init, As::Vararg{AbstractArray, N}) where {N}
```

`f` : ℝᴺ → ℝ の `mapreducethen` のバージョンで、次に `g` : ℝ → ℝ があり、すべての次元での還元が行われます。
