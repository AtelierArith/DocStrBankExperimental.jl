```
workspace = block_gmres!(workspace::BlockGmresWorkspace, B; kwargs...)
workspace = block_gmres!(workspace::BlockGmresWorkspace, B, X0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`block_gmres`](@ref)のキーワード引数です。キーワード引数`memory`は唯一の例外です。これは`block_gmres`によってのみサポートされており、`BlockGmresWorkspace`を作成するために必要です。後で変更することはできません。

`workspace`を作成する方法については、[`BlockGmresWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :block_gmres`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してブロックKrylov法をインプレースで実行できます。
