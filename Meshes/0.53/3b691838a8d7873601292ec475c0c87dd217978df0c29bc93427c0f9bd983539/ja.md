```
RectilinearGrid(x, y, z, ...)
RectilinearGrid{M,C}(x, y, z, ...)
```

ソートされた座標 `x`、`y`、`z`、... に頂点を持つ直交格子、マニフォールド `M`（デフォルトは `𝔼`）および CRS タイプ `C`（デフォルトは `Cartesian`）です。

## 例

`x` 次元で等間隔、`y` 次元で不規則な間隔の 2D 直交格子を作成します：

```julia
julia> x = 0.0:0.2:1.0
julia> y = [0.0, 0.1, 0.3, 0.7, 0.9, 1.0]
julia> RectilinearGrid(x, y)
```
