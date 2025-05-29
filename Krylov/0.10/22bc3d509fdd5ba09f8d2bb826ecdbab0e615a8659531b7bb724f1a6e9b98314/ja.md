```
workspace = bilq!(workspace::BilqWorkspace, A, b; kwargs...)
workspace = bilq!(workspace::BilqWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`bilq`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`BilqWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :bilq`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
