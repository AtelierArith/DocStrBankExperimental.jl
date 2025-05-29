```
Downscale(f₁, f₂, ..., fₙ)
```

与えられた因子 `f₁`, `f₂`, ..., `fₙ` によってグリッドの各次元をダウンサンプリングします。

結果の値は [`Transfer`](@ref) 変換を使用して取得されます。

# 例

```julia
Downscale(2, 2)
Downscale(3, 3, 2)
```
