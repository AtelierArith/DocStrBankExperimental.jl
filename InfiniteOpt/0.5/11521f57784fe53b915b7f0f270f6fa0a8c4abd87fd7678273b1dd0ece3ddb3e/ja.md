```
add_supports(prefs::AbstractArray{<:DependentParameterRef},
             supports::Vector{<:AbstractArray{<:Real}};
             [label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

`prefs`に追加のサポートポイントを追加します。サポートが無限のドメインに違反している場合、次元が正しく一致しない場合、`prefs`と`supports`のインデックスが異なる場合、またはすべての`prefs`が同じ依存無限パラメータコンテナからでない場合にエラーが発生します。

```julia
    add_supports(prefs::Vector{DependentParameterRef},
                 supports::Array{<:Real, 2};
                 [label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

依存無限パラメータのベクトル`prefs`のサポートを指定します。ここで、`supports`の行は`prefs`に対応し、列はサポートに対応します。これは上記の方法よりも効率的で、同じ理由でエラーが発生します。

**例**

```julia-repl
julia> add_supports(x, [[1], [1]])

julia> supports(x)
2×2 Array{Float64,2}:
 0.0  1.0
 0.0  1.0

julia> add_supports(x, ones(2, 1) * 0.5)

julia> supports(t)
2×3 Array{Float64,2}:
 0.0  1.0  0.5
 0.0  1.0  0.5
```
