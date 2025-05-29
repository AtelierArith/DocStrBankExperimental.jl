```
set_name(v::GenericVariableRef, s::AbstractString)
```

変数の名前属性を設定します。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> set_name(x, "x_foo")

julia> x
x_foo

julia> name(x)
"x_foo"
```
