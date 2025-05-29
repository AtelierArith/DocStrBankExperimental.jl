```
workspace = lsqr!(workspace::LsqrWorkspace, A, b; kwargs...)
```

この呼び出しでは、`kwargs`は[`lsqr`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`LsqrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :lsqr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
