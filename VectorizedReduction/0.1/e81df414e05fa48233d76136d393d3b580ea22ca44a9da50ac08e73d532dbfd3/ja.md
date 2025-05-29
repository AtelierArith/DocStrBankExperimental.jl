```
vtfindmin(f, As::Vararg{AbstractArray, N}; dims=:) where {N} -> (f(x,y,z,...), index)
```

引数の値とインデックスを返します。これにより、`f` : ℝᴺ → ℝ を次元 `dims` にわたって最小化します。スレッド対応。
