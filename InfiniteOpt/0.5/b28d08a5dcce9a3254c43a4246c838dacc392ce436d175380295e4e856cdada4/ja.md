```
SemiInfinite{V, VT <: VectorTuple} <: InfOptVariableType
```

半無限変数を作成するための `DataType` です。これは `@variable` に追加の引数として渡すことで、そのような変数を作成できます：

```julia
@variable(model, var_expr, SemiInfinite(inf_var, parameter_values...), kwargs...)
```

ここで `parameter_values` は、無限変数 `inf_var` に関連付けられた無限パラメータ参照の形式と一致し、実数値のサポートと/または無限パラメータの両方で構成されることができます。

**フィールド**

  * `infinite_variable_ref::V`
  * `parameter_values::VT`: 変数が依存する無限パラメータおよび/または無限パラメータサポート値。
