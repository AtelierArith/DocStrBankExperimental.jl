```
workspace = diom!(workspace::DiomWorkspace, A, b; kwargs...)
workspace = diom!(workspace::DiomWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`diom`](@ref)のキーワード引数です。キーワード引数`memory`は唯一の例外です。これは`diom`によってのみサポートされており、`DiomWorkspace`を作成するために必要です。後で変更することはできません。

`workspace`を作成する方法については、[`DiomWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :diom`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
