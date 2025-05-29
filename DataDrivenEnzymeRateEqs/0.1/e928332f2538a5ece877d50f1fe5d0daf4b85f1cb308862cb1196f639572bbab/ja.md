```
display_rate_equation(
rate_equation::Function,
metab_names::Tuple{Symbol,Vararg{Symbol}},
param_names::Tuple{Symbol,Vararg{Symbol}};
nt_param_removal_code = nothing
```

)

与えられた `rate_equation` 関数の記号的な反応速度方程式を返します。

# 引数

  * `rate_equation::Function`: 反応速度方程式の関数。
  * `metab_names::Tuple{Symbol,Vararg{Symbol}}`: メタボライトの名前。
  * `param_names::Tuple{Symbol,Vararg{Symbol}}`: パラメータの名前。
  * `nt_param_removal_code::NamedTuple`: 反応速度方程式から削除するパラメータの名前付きタプル。
