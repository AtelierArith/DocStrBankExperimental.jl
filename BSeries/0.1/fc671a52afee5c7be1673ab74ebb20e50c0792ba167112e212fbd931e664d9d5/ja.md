```
is_symplectic(series_integrator; kwargs...)::Bool
```

この関数は、時間積分法のB系列 `series_integrator` がシンプレクティック（2次不変量を保存する）であるかどうかをチェックします - `series_integrator` の [`order`](@ref) まで。

デフォルトでは、条件に入る係数の比較は `isequal` を使用して行われます。絶対/相対許容誤差 `atol`/`rtol` のようなキーワード引数が与えられたり、浮動小数点数が使用される場合、比較は `isapprox` を使用して行われ、キーワード引数 `kwargs...` が転送されます。

さらに [`order_of_symplecticity`](@ref) も参照してください。
