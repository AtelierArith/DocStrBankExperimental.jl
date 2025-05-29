```
build_basis(
    ham, address=starting_address(ham);
    cutoff, filter, sizelim, sort=false, kwargs...
) -> basis
build_basis(ham, addresses::AbstractVector; kwargs...)
```

線形演算子 `ham` のすべての基底要素を取得します。これは、アドレス `address` から到達可能な（非ゼロの行列要素を介して）要素をベクトルとして返します。単一のアドレスの代わりに、`addresses` のベクトルを渡すことができます。行列は返されず、その目的には [`BasisSetRepresentation`](@ref) を使用してください。

エネルギーカットオフを提供すると、対角要素が `cutoff` より大きいアドレスはスキップされます。代わりに、任意の `filter` 関数を使用することもできます。引数として渡されたアドレスはフィルタリングされません。

`max_depth` を提供すると、基底のサイズが制限され、ハミルトニアンを介して `starting_address` に接続されているアドレスのみを訪問します。同様に、`minimum_size` を提供すると、基底が少なくとも `minimum_size` の長さに達した後、構築プロセスが停止します。

最大基底サイズ `sizelim` を設定することができ、`ham` の期待される次元が `sizelim` より大きい場合にエラーが発生します。これは、メモリが懸念される場合に役立ちます。これらのオプションはデフォルトで無効になっています。

!!! warning
    ```
    基底が返される順序は任意であり、非決定的です。順序が重要な場合は
    `sort=true` を使用してください。
    ```

