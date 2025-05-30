```
randcycle([rng=default_rng(),] n::Integer)
```

長さ `n` のランダムな循環置換を構築します。オプションの `rng` 引数は乱数生成器を指定します。結果の要素型は `n` の型と同じです。

!!! compat "Julia 1.1"
    Julia 1.1 では `randcycle` は `eltype(v) == typeof(n)` のベクトル `v` を返しますが、Julia 1.0 では `eltype(v) == Int` です。


# 例

```jldoctest
julia> randcycle(MersenneTwister(1234), 6)
6-element Vector{Int64}:
 3
 5
 4
 6
 1
 2
```
