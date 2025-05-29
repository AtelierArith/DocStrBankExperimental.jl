```
linear_region(x, y; kwargs...) -> (region, slope)
```

[`linear_regions`](@ref)を呼び出し、最大の線形領域（`x`のインデックスの`UnitRange`）とそれに対応する傾きを特定して返します。

キーワード`dxi, tol`はそのまま[`linear_regions`](@ref)に伝播されます。キーワード`ignore_saturation = true`は、曲線`y(x)`の開始と終了で（時々）発生する飽和を無視します。ここでは曲線が平坦になります。キーワード`sat = 0.01`は、何が飽和であるかを決定します（`abs(y[i]-y[i+1])<sat`の間、私たちは飽和領域にいます）。

キーワード`warning = true`は、線形領域が利用可能なx軸の1/3未満の場合に警告を印刷します。
