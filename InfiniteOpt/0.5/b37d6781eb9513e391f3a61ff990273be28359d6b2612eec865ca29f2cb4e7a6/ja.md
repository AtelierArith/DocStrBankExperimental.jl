```
JuMP.add_variable(model::InfiniteModel, var::PointVariable,
                  [name::String = ""])::GeneralVariableRef
```

`JuMP.add_variable` 関数を拡張して `PointVariable` 変数タイプに対応させます。無限モデル `model` に変数を追加し、[`GeneralVariableRef`](@ref) を返します。主にコンストラクタマクロ `@variable` の内部関数として意図されています。ただし、`JuMP.build_variable` と組み合わせて無限モデルオブジェクトに変数を追加するためにも使用できます。無効な無限変数参照が `var` に含まれている場合はエラーが発生します。

**例**

```julia-repl
julia> @infinite_parameter(m, t in [0, 10]);

julia> info = VariableInfo(false, 0, false, 0, false, 0, true, 0, false, false);

julia> inf_var = build_variable(error, info, Infinite(t));

julia> ivref = add_variable(m, inf_var, "var_name")
var_name(t)

julia> pt_var = build_variable(error, info, Point(ivref, 0.5));

julia> pvref = add_variable(m, pt_var, "var_alias")
var_alias
```
