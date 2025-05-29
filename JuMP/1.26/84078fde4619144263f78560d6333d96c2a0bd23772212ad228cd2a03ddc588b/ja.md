```
index(v::GenericVariableRef)::MOI.VariableIndex
```

`v` に対応する変数のインデックスを MOI バックエンドから返します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> index(x)
MOI.VariableIndex(1)
```
