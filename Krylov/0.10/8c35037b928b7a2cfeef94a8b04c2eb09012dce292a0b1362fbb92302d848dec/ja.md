```
workspace = qmr!(workspace::QmrWorkspace, A, b; kwargs...)
workspace = qmr!(workspace::QmrWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`qmr`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`QmrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :qmr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
