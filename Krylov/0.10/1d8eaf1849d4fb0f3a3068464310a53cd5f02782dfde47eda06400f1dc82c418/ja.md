```
workspace = cg_lanczos!(workspace::CgLanczosWorkspace, A, b; kwargs...)
workspace = cg_lanczos!(workspace::CgLanczosWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`cg_lanczos`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CgLanczosWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :cg_lanczos`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
