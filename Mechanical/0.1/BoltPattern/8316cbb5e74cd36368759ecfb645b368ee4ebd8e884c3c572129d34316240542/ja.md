```
rectangle(;x_dist, y_dist, Nx=2, Ny=2)
```

長方形のボルトパターンのxおよびy座標を計算します。

`x_dist`はx方向の長方形ボルトパターンの幅です。 `y_dist`はy方向の長方形ボルトパターンの高さです。 `Nx`と`Ny`はそれぞれボルトパターンの幅と高さに沿ったボルトの数です。単位は`Unitful`パッケージに準拠する必要があります。

# 例

```julia-repl
julia> using Unitful: mm
julia> rectangle(x_dist = 250mm, y_dist = 125mm, Nx = 3, Ny=4)
(Quantity{Float64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}  [-125.0 mm, -125.0 mm, -125.0 mm, -125.0 mm, 0.0 mm, 0.0 mm, 125.0 mm, 125.0 mm, 125.0 mm, 125.0 mm], Quantity{Float64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}  [62.5 mm, 20.83333333333334 mm, -20.83333333333333 mm, -62.5 mm, 62.5 mm, -62.5 mm, 62.5 mm, 20.83333333333334 mm, -20.83333333333333 mm, -62.5 mm])
```
