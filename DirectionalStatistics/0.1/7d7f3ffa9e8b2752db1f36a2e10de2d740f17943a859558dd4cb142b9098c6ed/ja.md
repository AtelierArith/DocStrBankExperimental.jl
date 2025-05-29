コレクション内の最も遠い点のペアのインデックスを選択します。点は実数（1d）、複素数（2d）、または任意のベクトルとして指定できます。

```jldoctest
julia> most_distant_points_ix([1, 2, 3])
(3, 1)

julia> most_distant_points_ix([0, 1, 1+1im])
(3, 1)

julia> most_distant_points_ix([[0, 0], [0, 1], [1, 1]])
(3, 1)
```
