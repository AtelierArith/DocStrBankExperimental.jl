```
vfindmax(f, As::Vararg{AbstractArray, N}; dims=:) where {N} -> (f(x,y,z,...), index)
```

引数の値とインデックスを返し、`f` : ℝᴺ → ℝ を次元 `dims` にわたって最大化します。これは、Julia Base に存在する機能を拡張したものです。
