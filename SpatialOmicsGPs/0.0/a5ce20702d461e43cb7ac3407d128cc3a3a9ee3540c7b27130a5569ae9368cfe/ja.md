```
spatialde_param_inference(y,x::Union{RowVecs, ColVecs},n::Int; covariates = [], mean = true, lambda_tol = 1e-3)
```

SpatialDEモデルのパラメータ推定を、位置`x`で観測された`y`のすべての変数（列）に対して行います。これは、二乗指数カーネルと`n`の長さスケールのグリッドを使用します。入力`x`は、`KernelFunctions`パッケージの`RowVecs`または`ColVecs`型である必要があります。この関数は、すべての変数に対する最適な分散パラメータと長さスケールインデックス、および使用された長さスケールのグリッドを返します。
