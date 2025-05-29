```
vargmax(f, As::Vararg{AbstractArray, N}; dims=:) where {N}
```

引数のインデックスを返します。これは、次元 `dims` にわたって `f` : ℝᴺ → ℝ を最大化します。スレッド化されています。
