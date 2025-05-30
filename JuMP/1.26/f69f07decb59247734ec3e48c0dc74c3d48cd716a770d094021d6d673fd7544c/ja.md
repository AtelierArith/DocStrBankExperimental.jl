```
set_binary(v::GenericVariableRef)
```

変数 `v` に対して、値が集合 $\{0,1\}$ に属するという制約を追加します。

関連情報としては [`BinaryRef`](@ref), [`is_binary`](@ref), [`unset_binary`](@ref) があります。

## 例

```jldoctest
julia> model = Model();

julia> @variable(model, x);

julia> is_binary(x)
false

julia> set_binary(x)

julia> is_binary(x)
true
```
