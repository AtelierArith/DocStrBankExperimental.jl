```
vargmin(f, As::Vararg{AbstractArray, N}; dims=:) where {N}
```

引数のインデックスを返します。これにより、`f` : ℝᴺ → ℝ を `dims` の次元で最小化します。これは、Julia Base に存在する機能を拡張したものです。
