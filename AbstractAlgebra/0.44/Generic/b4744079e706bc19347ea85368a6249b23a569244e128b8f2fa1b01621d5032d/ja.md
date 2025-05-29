```
downscale(a::Generic.LaurentSeriesElem{T}, n::Int) where T <: RingElement
```

基礎となる多項式を$n$の因子で膨らませます。これはパディングのためにゼロ係数を挿入します。$a$のスケール因子が$n$で割り切れると仮定します。
