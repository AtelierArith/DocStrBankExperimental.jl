```
workspace = block_minres!(workspace::BlockMinresWorkspace, B; kwargs...)
workspace = block_minres!(workspace::BlockMinresWorkspace, B, X0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`block_minres`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`BlockMinresWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :block_minres`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してブロックKrylov法をインプレースで実行できます。
