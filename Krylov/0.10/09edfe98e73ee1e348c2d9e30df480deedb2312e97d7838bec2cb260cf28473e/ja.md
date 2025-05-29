```
workspace = craigmr!(workspace::CraigmrWorkspace, A, b; kwargs...)
```

この呼び出しでは、`kwargs`は[`craigmr`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CraigmrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :craigmr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
