```
workspace = cr!(workspace::CrWorkspace, A, b; kwargs...)
workspace = cr!(workspace::CrWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`cr`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :cr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
