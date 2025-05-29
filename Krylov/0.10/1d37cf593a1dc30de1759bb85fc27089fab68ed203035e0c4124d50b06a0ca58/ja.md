```
workspace = bilqr!(workspace::BilqrWorkspace, A, b, c; kwargs...)
workspace = bilqr!(workspace::BilqrWorkspace, A, b, c, x0, y0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`bilqr`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`BilqrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :bilqr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylov法をインプレースで実行できます。
