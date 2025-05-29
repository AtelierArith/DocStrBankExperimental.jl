```
y = polyval(p::AbstractArray, x::Union{AbstractArray, Number})
```

多項式 p を x の各点で評価します。引数 p は長さ n+1 のベクトルで、その要素は n 次多項式の係数（冪の昇順）です：
