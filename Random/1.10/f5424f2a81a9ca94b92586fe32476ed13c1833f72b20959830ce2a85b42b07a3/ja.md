```
randperm!([rng=default_rng(),] A::Array{<:Integer})
```

`A`に長さ`length(A)`のランダムな順列を構築します。オプションの`rng`引数は乱数生成器を指定します（[Random Numbers](@ref)を参照）。任意のベクトルをランダムに順列するには、[`shuffle`](@ref)または[`shuffle!`](@ref)を参照してください。

# 例

```jldoctest
julia> randperm!(MersenneTwister(1234), Vector{Int}(undef, 4))
4-element Vector{Int64}:
 2
 1
 4
 3
```
