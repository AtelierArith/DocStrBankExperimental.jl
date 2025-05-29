コレクション内の最も遠い点のペアを選択します。点は実数（1d）、複素数（2d）、または任意のベクトルとして指定できます。

```jldoctest
julia> most_distant_points([1, 2, 3])
(3, 1)

julia> most_distant_points([0, 1, 1+1im])
(1 + 1im, 0 + 0im)

julia> most_distant_points([[0, 0], [0, 1], [1, 1]])
([1, 1], [0, 0])
```
