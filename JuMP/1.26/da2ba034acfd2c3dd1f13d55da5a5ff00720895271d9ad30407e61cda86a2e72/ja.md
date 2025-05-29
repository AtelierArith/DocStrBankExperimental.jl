```
is_integer(v::GenericVariableRef)
```

`v` が整数に制約されている場合は `true` を返します。

関連情報としては [`IntegerRef`](@ref), [`set_integer`](@ref), [`unset_integer`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_integer(x)
false

julia> set_integer(x)

julia> is_integer(x)
true
```
