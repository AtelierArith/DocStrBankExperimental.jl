```
parameter_by_name(model::InfiniteModel,
                  name::String)::Union{GeneralVariableRef, Nothing}
```

パラメータ名に関連付けられたパラメータ参照を返します。同じ名前のパラメータが複数ある場合はエラーになります。そのような名前が存在しない場合は何も返しません。

**例**

```julia-repl
julia> parameter_by_name(model, "t")
t
```
