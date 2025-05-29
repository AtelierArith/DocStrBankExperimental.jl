```
localgrid((xs, ys, ...), perm = NoPermutation()) -> LocalRectilinearGrid
```

一組の直交座標 `(xs, ys, ...)` から [`LocalRectilinearGrid`](@ref) を作成します。各要素は `AbstractVector` です。

オプションで、座標が反復される順序を変更するために静的な置換（`Permutation(2, 1, 3)` のように）を渡すことができます。
