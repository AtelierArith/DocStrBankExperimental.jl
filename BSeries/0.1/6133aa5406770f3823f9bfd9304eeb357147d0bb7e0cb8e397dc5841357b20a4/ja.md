```
order_of_symplecticity(series_integrator; kwargs...)
```

B系列 `series_integrator` のシンプレクティシティの次数を決定します。つまり、二次不変量が保存される次数です。デフォルトでは、条件に入る係数の比較は `isequal` を使用して行われます。絶対/相対許容誤差 `atol`/`rtol` のようなキーワード引数が与えられたり、浮動小数点数が使用される場合、比較は `isapprox` を使用して行われ、キーワード引数 `kwargs...` は転送されます。

関連情報としては [`is_symplectic`](@ref), [`order`](@ref), [`order_of_accuracy`](@ref) があります。
