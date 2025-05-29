```
JuMP.variable_by_name(model::InfiniteModel,
                      name::String)::Union{GeneralVariableRef, Nothing}
```

`JuMP.variable_by_name`を`InfiniteModel`オブジェクト用に拡張します。変数名に関連付けられた変数参照を返します。同じ名前の変数が複数ある場合はエラーを返します。そのような名前が存在しない場合は何も返しません。

**例**

```julia-repl
julia> variable_by_name(m, "var_name")
var_name

julia> variable_by_name(m, "fake_name")

```
