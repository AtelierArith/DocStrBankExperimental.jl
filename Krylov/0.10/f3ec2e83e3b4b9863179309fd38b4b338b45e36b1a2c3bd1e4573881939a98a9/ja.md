```
workspace = usymqr!(workspace::UsymqrWorkspace, A, b, c; kwargs...)
workspace = usymqr!(workspace::UsymqrWorkspace, A, b, c, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`usymqr`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`UsymqrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :usymqr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylov法をインプレースで実行できます。
