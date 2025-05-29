```
Point{V, VT <: VectorTuple} <: InfOptVariableType
```

点変数を作成するための `DataType` です。これは `@variable` に追加の引数として渡すことができ、そのような変数を作成します：

```julia
@variable(model, var_expr, Point(inf_var, parameter_values...), args..., 
          kwargs...)
```

ここで `parameter_values` は無限変数 `inf_var` に関連付けられた無限パラメータ参照の形式と一致し、実数値のサポートの両方で構成されることができます。

**フィールド**

  * `infinite_variable_ref::V`
  * `parameter_values::VT`: 変数が依存する無限パラメータサポート値。
