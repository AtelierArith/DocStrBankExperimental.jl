```
vtfindmax(f, As::Vararg{AbstractArray, N}; dims=:) where {N} -> (f(x,y,z,...), index)
```

引数の値とインデックスを返します。これにより、`f` : ℝᴺ → ℝ が次元 `dims` にわたって最大化されます。スレッド対応。
