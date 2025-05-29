```
circle(;r, N=4, theta_start=0)
```

円形ボルトパターンのxおよびy座標を計算します。

`r`はボルトパターンの半径で、`N`はボルトパターン内のボルトの数です。`theta_start`は、パターン内の最初のボルトまでのy軸から時計回りに測定された角度です。単位は`Unitful`パッケージに準拠する必要があります。

# 例

```julia-repl
julia> using Unitful: mm
julia> circle(r=100mm, N=3)
(Quantity{Float64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}  [6.123233995736766e-15 mm, 86.60254037844386 mm, -86.60254037844388 mm], Quantity{Float64, 𝐋, Unitful.FreeUnits{(mm,), 𝐋, nothing}}  [100.0 mm, -50.0 mm, -49.99999999999999 mm])
```
