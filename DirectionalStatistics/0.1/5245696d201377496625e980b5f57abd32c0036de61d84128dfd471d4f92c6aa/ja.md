点の集合の幾何学的中央値。点は実数（1d）、複素数（2d）、または任意のベクトルとして指定できます。

詳細は[https://en.wikipedia.org/wiki/Geometric_median]を参照してください。

```jldoctest
julia> geometric_median([1, 2, 3])
2.0

julia> geometric_median([0, 1, 1im, 1+1im]) ≈ 0.5+0.5im
true

julia> geometric_median([[0, 0], [0, 1], [1, 0], [1, 1]]) ≈ [0.5, 0.5]
true
```
