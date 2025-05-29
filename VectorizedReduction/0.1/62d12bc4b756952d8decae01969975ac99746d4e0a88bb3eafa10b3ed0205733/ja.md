```
vargmax(f, As::Vararg{AbstractArray, N}; dims=:) where {N}
```

引数のインデックスを返します。これにより、次元 `dims` にわたって `f` : ℝᴺ → ℝ を最大化します。これは、Julia Base に存在する機能を拡張したものです。
