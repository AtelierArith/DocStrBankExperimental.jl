```
allocate_matrix(MatrixType, dh::DofHandler, args...; kwargs...)
```

DofHandler `dh` から `MatrixType` 型の行列を割り当てます。

これは便利なメソッドであり、次のように同等です：

`julia sp = init_sparsity_pattern(dh) add_sparsity_entries!(sp, dh, args...; kwargs...) allocate_matrix(MatrixType, sp)``

サポートされている行列型については [`allocate_matrix`](@ref allocate_matrix(::Type{<:Any}, ::SparsityPattern)) を参照し、サポートされている引数 `args` とキーワード引数 `kwargs` の詳細については [`init_sparsity_pattern`](@ref) を参照してください。

!!! note
    複数のスパース行列が必要な場合（例：剛性行列と質量行列）、このメソッドを使用するのではなく、スパースパターンを明示的に作成する方が効率的です。つまり、次のように使用します。

    ```julia
    sp = init_sparsity_pattern(dh)
    add_sparsity_entries!(sp, dh)
    K = allocate_matrix(sp)
    M = allocate_matrix(sp)
    ```

    代わりに

    ```julia
    K = allocate_matrix(dh)
    M = allocate_matrix(dh)
    ```

    一部の行列型では、インスタンス化された行列を `copy` することも可能です（`M = copy(K)`）。

