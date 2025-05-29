```
show_constraints_summary(io::IO, model::AbstractModel)
```

`io`に制約の数の概要を書き込みます。

## 拡張

`AbstractModel`はこのメソッドを実装する必要があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x >= 0);

julia> show_constraints_summary(stdout, model)
`VariableRef`-in-`MathOptInterface.GreaterThan{Float64}`: 1 constraint
```
