```
sparsity_pattern(result::AbstractColoringResult)
```

初めに[`coloring`](@ref)に渡された行列を、変更せずに返します。

!!! note
    この行列は必ずしも`SparseMatrixCSC`ではなく、`Bool`エントリを持つ必要もありません。

