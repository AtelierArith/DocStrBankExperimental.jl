```
Deriv{V, P} <: InfOptVariableType
```

導関数変数を作成するための `DataType` です。これは、次のように `@variable` に追加の引数として渡すことができます：

```julia
@variable(model, var_expr, Deriv(inf_var, inf_par), kwargs...)
```

ここで `inf_var` は操作される無限変数であり、`inf_par` は導関数が定義される無限パラメータです。

**フィールド**

  * `argument::V`: 操作される無限変数。
  * `operator_parameter::P:` 導関数を決定する無限パラメータ。
