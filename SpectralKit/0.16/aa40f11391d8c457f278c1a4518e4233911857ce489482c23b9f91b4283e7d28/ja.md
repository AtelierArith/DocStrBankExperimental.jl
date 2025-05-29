```julia
Chebyshev(grid_kind, N)

```

`N` チェビシェフ多項式（第一種）を $[-1, 1]$ 上で、`grid_kind` に関連するグリッドと共に。

# 例

```julia
basis = Chebyshev(InteriorGrid(), 10)
```
