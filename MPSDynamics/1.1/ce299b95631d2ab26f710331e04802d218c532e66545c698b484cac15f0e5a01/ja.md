```
elementmps(A, el...)
```

MPS `A` の物理状態のセット `el...` の要素を返します。

# 例

```julia-repl
julia> A = chainmps(6, [2,4], 1);

julia> elementmps(A, 1, 2, 1, 1, 1, 1)
0.7071067811865475

julia> elementmps(A, 1, 1, 1, 2, 1, 1)
0.7071067811865475

julia> elementmps(A, 1, 2, 1, 2, 1, 1)
0.0

julia> elementmps(A, 1, 1, 1, 1, 1, 1)
0.0
```
