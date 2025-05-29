```
workspace = minres_qlp!(workspace::MinresQlpWorkspace, A, b; kwargs...)
workspace = minres_qlp!(workspace::MinresQlpWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`minres_qlp`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`MinresQlpWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :minres_qlp`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
