```
spatialde_varpars_all(y,x::Union{RowVecs, ColVecs},n::Int; covariates = [], mean = true, lambda_tol = 1e-3)
```

`y`で観測されたすべての変数（列）の空間分散パラメータを、`x`の位置で計算します。FaST-LMMを使用し、二乗指数カーネルと長さスケールのグリッドを用います。入力`x`は、`KernelFunctions`パッケージの`RowVecs`または`ColVecs`型である必要があります。
