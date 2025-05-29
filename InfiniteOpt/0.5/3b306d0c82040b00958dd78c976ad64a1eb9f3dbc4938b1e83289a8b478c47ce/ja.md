```
JuMP.add_variable(model::InfiniteModel, var::JuMP.ScalarVariable,
                  [name::String = ""])::GeneralVariableRef
```

`JuMP.add_variable` 関数を拡張して有限（スカラー）変数タイプに対応させます。無限モデル `model` に変数を追加し、[`GeneralVariableRef`](@ref) を返します。主にコンストラクタマクロ `@variable` の内部関数として意図されています。ただし、`JuMP.build_variable` と組み合わせて無限モデルオブジェクトに有限変数を追加するためにも使用できます。

**例**

```julia-repl
julia> f_var = build_variable(error, info);

julia> fvref = add_variable(m, f_var, "var_name")
var_name
```
