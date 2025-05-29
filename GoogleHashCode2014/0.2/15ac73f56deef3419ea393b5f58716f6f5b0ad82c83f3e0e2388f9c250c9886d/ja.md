```
random_walk(rng::Random.AbstractRNG, city::City)
random_walk(city:::City)
```

各車両が出発点からランダムウォークを行うことによって、`city`から[`Solution`](@ref)を計算して返します。

!!! tip
    特定のシードを持つ乱数生成器（例：`Random.MersenneTwister(0)`）を渡すことで、再現可能な結果を得ることができます。そうでない場合は、グローバルな乱数生成器が使用され、実行ごとに結果が異なります。


# 例

```jldoctest
julia> using GoogleHashCode2014, Random

julia> city = read_city();

julia> rng = Random.MersenneTwister(0);

julia> solution = random_walk(rng, city)
Solution with 8 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366, 3707]
```
