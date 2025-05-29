```
total_distance(solution::Solution, city::City)
```

`city`のストリートデータに基づいて、`solution`内のすべての旅程によって移動した総距離を計算します。

!!! warning
    複数回訪れたストリートや両方向でのストリートは、1回のみカウントされます。


# 例

```jldoctest
julia> using GoogleHashCode2014, Random

julia> city = read_city();

julia> rng = Random.MersenneTwister(0);

julia> solution = random_walk(rng, city)
Solution with 8 itineraries of lengths [3810, 3277, 3779, 3278, 3451, 3697, 4366, 3707]

julia> total_distance(solution, city)
752407
```
