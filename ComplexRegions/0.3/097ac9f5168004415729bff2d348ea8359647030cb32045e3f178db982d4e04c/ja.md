```
arclength(X)
```

曲線またはパス `X` の弧長を取得または計算します。

# 例

```
julia> ellipse = ClosedCurve( t->cos(t)+2im*sin(t), 0,2π );
julia> arclength(ellipse)  # 約10桁の精度
9.688448219981513
```
