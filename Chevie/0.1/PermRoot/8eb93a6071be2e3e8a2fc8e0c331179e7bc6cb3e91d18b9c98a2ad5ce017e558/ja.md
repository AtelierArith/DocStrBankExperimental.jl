`reflection_eigenvalues(W)` または `refleigen(W)`

`W` をベクトル空間 `V` 上の反射群とします。`reflection_eigenvalues(W)` は、`W` の各共役類代表 `x` に対して（`classreps` を参照）、`V` 上の `x` の固有値を `Root1` のリストとして返します。

```julia-repl
julia> refleigen(coxgroup(:B,2))
5-element Vector{Vector{Root1}}:
 [1, 1]
 [-1, 1]
 [-1, -1]
 [-1, 1]
 [ζ₄³, ζ₄]
```
