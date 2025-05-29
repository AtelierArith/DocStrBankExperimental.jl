```
InfOptSensitivityReport
```

`InfiniteOpt`の`JuMP.SensitivityReport`のラッパー`DataType`。これらはオプティマイザーモデルに基づいて生成され、[`lp_sensitivity_report`](@ref JuMP.lp_sensitivity_report(::InfiniteModel))を使用して作成されるべきです。一度作成されると、これらは変数および/または制約に関する感度を取得するためにインデックス指定できます。これらのインデックス指定構文は次のとおりです：

```julia
report[ref::[GeneralVariableRef/InfOptConstraintRef]; 
       [label::Type{<:AbstractSupportLabel} = PublicLabel,
       ndarray::Bool = false, kwargs...]]
```

これは、[`optimizer_model_variable`](@ref)および[`optimizer_model_constraint`](@ref)を適切に拡張することによって、ユーザー定義のオプティマイザーモデル拡張で有効になります。

**フィールド**

  * `opt_report::JuMP.SensitivityReport`: オプティマイザーモデルからキャプチャされたLP感度。
