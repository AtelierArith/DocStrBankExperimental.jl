```
set_supports(prefs::AbstractArray{<:DependentParameterRef},
             supports::Vector{<:AbstractArray{<:Real}};
             [force::Bool = false,
             label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

`prefs`のサポートポイントを指定します。サポートが無限のドメインに違反している場合、次元が正しく一致しない場合、`prefs`と`supports`のインデックスが異なる場合、すべての`prefs`が同じ依存無限パラメータコンテナからでない場合、既存のサポートがあり`force = false`の場合にエラーが発生します。依存関係を破壊しないために、可能であれば`add_supports`を使用することが強く推奨されます。

```julia
    set_supports(prefs::Vector{DependentParameterRef},
                 supports::Array{<:Real, 2};
                 [force::Bool = false,
                 label::Type{<:AbstractSupportLabel} = UserDefined])::Nothing
```

依存無限パラメータのベクトル`prefs`のサポートを指定します。ここで、`supports`の行は`prefs`に対応し、列はサポートに対応します。これは上記の方法よりも効率的で、同じ理由でエラーが発生します。

**例**

```julia-repl
julia> set_supports(y, [[0, 1], [0, 1]])

julia> set_supports(x, [0 1; 0 1])

julia> supports(x)
2×2 Array{Float64,2}:
 0.0  1.0
 0.0  1.0
```
