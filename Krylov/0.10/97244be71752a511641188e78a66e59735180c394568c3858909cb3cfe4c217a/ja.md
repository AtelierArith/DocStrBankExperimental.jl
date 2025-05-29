```
workspace = cgs!(workspace::CgsWorkspace, A, b; kwargs...)
workspace = cgs!(workspace::CgsWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`cgs`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CgsWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :cgs`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
