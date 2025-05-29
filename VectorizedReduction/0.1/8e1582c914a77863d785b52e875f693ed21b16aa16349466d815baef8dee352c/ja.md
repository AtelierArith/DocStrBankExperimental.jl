```
vargmin(f, As::Vararg{AbstractArray, N}; dims=:) where {N}
```

引数のインデックスを返します。これにより、`f` : ℝᴺ → ℝ を `dims` の次元で最小化します。スレッド対応。
