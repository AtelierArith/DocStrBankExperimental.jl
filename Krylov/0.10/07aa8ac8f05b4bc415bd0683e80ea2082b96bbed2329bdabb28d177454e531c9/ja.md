```
workspace = crls!(workspace::CrlsWorkspace, A, b; kwargs...)
```

この呼び出しでは、`kwargs`は[`crls`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CrlsWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :crls`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
