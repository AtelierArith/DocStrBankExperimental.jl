```
vtmapreduce(f, op, init, As::Vararg{AbstractArray, N}; dims=:, init) where {N}
```

`f` のバージョン : ℝᴺ → ℝ、`dims` に対する縮約。スレッド対応。
