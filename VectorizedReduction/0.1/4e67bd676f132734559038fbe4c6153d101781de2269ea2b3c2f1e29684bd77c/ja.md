```
vfindmin(f, As::Vararg{AbstractArray, N}; dims=:) where {N} -> (f(x,y,z,...), index)
```

引数の値とインデックスを返します。これにより、`f` : ℝᴺ → ℝ を `dims` の次元で最小化します。これは、Julia Base に存在する機能を拡張したものです。
