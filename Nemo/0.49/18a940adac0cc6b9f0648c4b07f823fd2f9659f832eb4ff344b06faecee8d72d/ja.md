```
downscale(a::ZZLaurentSeriesRingElem, n::Int)
```

基礎となる多項式を $n$ の因子で膨張させます。これはパディングのためにゼロ係数を挿入します。$a$ のスケール因子が $n$ で割り切れると仮定します。
