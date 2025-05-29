`ranking(P)`

ここで `P` は `Poset` または `CPoset` です。部分順序集合は、レシピ

`ρ(x)=0` もし `x∈minima(P)` の場合、`ρ(y)=ρ(x)+1` もし `y` が `x` の即時後継である場合

が明確に定義された関数 `ρ` を与える場合にランク付けされていると言います。したがって、`ρ` は `P` のランク付けと呼ばれます。関数 `ranking` は、`P` にランク付けがある場合、`P` の要素に対して `x` が走るときの `ρ(x)` のベクトルを返し、そうでない場合は `nothing` を返します。

部分順序集合 `P` は、すべての最大鎖が同じ長さを持つ場合、または同等に `P` がランク付けされていて `allequal(ranking(P)[maxima(P)])` である場合にグレーディッドと呼ばれます。

```julia-repl
julia> ranking(Poset(:partitionsdominance,6))
11-element Vector{Int64}:
 0
 1
 2
 3
 3
 4
 5
 5
 6
 7
 8

julia> ranking(Poset(:partitionsdominance,7)) # not ranked

```
