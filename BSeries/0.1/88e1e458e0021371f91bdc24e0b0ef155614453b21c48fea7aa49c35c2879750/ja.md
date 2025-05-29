```
order_of_accuracy(series; kwargs...)
```

B系列 `series` の精度の次数を決定します。デフォルトでは、正確な解の係数との比較は `isequal` を使用して行われます。絶対/相対許容誤差 `atol`/`rtol` などのキーワード引数が指定されるか、浮動小数点数が使用される場合、比較は `isapprox` を使用して行われ、キーワード引数 `kwargs...` が転送されます。

関連情報は [`order`](@ref)、[`ExactSolution`](@ref)、[`order_of_symplecticity`](@ref) を参照してください。 ```
