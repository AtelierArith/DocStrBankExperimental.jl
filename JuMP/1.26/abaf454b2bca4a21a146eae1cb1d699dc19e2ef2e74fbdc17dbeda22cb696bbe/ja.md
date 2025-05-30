```
unregister(model::GenericModel, key::Symbol)
```

`model` から名前 `key` を登録解除して、新しい変数、制約、または式を同じキーで作成できるようにします。

これは `model[key]` のオブジェクトを削除するものではなく、単に `model[key]` の参照を削除するだけです。オブジェクトを削除するには、[`delete`](@ref) も使用してください。

関連情報: [`delete`](@ref), [`object_dictionary`](@ref).

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x)
x

julia> @variable(model, x)
ERROR: An object of name x is already attached to this model. If this
    is intended, consider using the anonymous construction syntax, for example,
    `x = @variable(model, [1:N], ...)` where the name of the object does
    not appear inside the macro.

    Alternatively, use `unregister(model, :x)` to first unregister
    the existing name from the model. Note that this will not delete the
    object; it will just remove the reference at `model[:x]`.

Stacktrace:
[...]

julia> num_variables(model)
1

julia> unregister(model, :x)

julia> @variable(model, x)
x

julia> num_variables(model)
2
```
