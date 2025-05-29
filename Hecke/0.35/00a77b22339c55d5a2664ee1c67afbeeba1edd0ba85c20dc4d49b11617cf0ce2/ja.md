```
close_vectors(L:ZZLat, v:Vector, [lb,], ub; check::Bool = false)
                                        -> Vector{Tuple{Vector{Int}}, QQFieldElem}
```

すべてのタプル `(x, d)` を返します。ここで `x` は `L` の要素であり、`d = b(v - x, v - x) <= ub` です。`lb` が提供されている場合、`lb <= d` も満たされます。

`filter` が `nothing` でない場合、`filter(x)` が `true` に評価される `x` のみが返されます。

デフォルトでは、`L` が正定値であるかどうかがチェックされます。これを無効にするには `check = false` を設定します。

入力と出力はどちらも `L` の基底行列に関してです。

# 例

```jldoctest
julia> L = integer_lattice(matrix(QQ, 2, 2, [1, 0, 0, 2]));

julia> close_vectors(L, [1, 1], 1)
3-element Vector{Tuple{Vector{ZZRingElem}, QQFieldElem}}:
 ([2, 1], 1)
 ([0, 1], 1)
 ([1, 1], 0)

julia> close_vectors(L, [1, 1], 1, 1)
2-element Vector{Tuple{Vector{ZZRingElem}, QQFieldElem}}:
 ([2, 1], 1)
 ([0, 1], 1)
```
