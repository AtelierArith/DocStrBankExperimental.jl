```
has_start_value(variable::AbstractVariableRef)
```

変数に開始値が設定されている場合は `true` を返し、そうでない場合は `false` を返します。

参照: [`start_value`](@ref), [`set_start_value`](@ref).

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x, start = 1.5);

julia> @variable(model, y);

julia> has_start_value(x)
true

julia> has_start_value(y)
false

julia> start_value(x)
1.5

julia> set_start_value(y, 2.0)

julia> has_start_value(y)
true

julia> start_value(y)
2.0
```
