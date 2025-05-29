```
init_sparsity_pattern(dh::DofHandler; nnz_per_row::Int)
```

空の [`SparsityPattern`](@ref) を `ndofs(dh)` 行と `ndofs(dh)` 列で初期化します。

# キーワード引数

  * `nnz_per_row`: パターンに追加される行ごとの非ゼロエントリの数に関するメモリ最適化のヒント。
