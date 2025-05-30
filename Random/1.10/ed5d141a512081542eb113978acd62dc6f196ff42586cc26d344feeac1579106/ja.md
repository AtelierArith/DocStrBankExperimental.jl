```
randcycle!([rng=default_rng(),] A::Array{<:Integer})
```

`A`に長さ`length(A)`のランダムな循環置換を構築します。オプションの`rng`引数は乱数生成器を指定します。詳細は[Random Numbers](@ref)を参照してください。

# 例

```jldoctest
julia> randcycle!(MersenneTwister(1234), Vector{Int}(undef, 6))
6-element Vector{Int64}:
 3
 5
 4
 6
 1
 2
```
