```
<|(f, args)
```

関数を次の引数または引数のタプルに適用します。[`|>`](@ref)の逆として機能し、部分関数と組み合わせることで、代替の低括弧関数チェイニング構文に特に便利です。

# 例

```@jldoctest
julia> using PartialFunctions

julia> isdigit <| '1'
true

julia> (+) <| (2, 3)...
5

julia> map $ Int <| [1.0, 2.0, 3.0]
3-element Vector{Int64}:
 1
 2
 3
```
