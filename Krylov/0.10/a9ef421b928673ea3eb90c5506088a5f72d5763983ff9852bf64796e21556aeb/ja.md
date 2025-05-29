```
workspace = cgls!(workspace::CglsWorkspace, A, b; kwargs...)
```

この呼び出しでは、`kwargs`は[`cgls`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CglsWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :cgls`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylov法をインプレースで実行できます。
