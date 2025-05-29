```
JuMP.add_variable(model::InfiniteModel, var::InfiniteVariable,
                  [name::String = ""])::GeneralVariableRef
```

`JuMP.add_variable` 関数を拡張して無限変数タイプに対応します。無限モデル `model` に変数を追加し、[`GeneralVariableRef`](@ref) を返します。主にコンストラクタマクロ `@variable` の内部関数として意図されています。ただし、`JuMP.build_variable` と組み合わせて無限モデルオブジェクトに無限変数を追加するためにも使用できます。無効なパラメータ参照が `var` に含まれている場合はエラーが発生します。

**例**

```julia-repl
julia> @infinite_parameter(m, t in [0, 10]);

julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> inf_var = build_variable(error, info, Infinite(t));

julia> ivref = add_variable(m, inf_var, "var_name")
var_name(t)
```
