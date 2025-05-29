```
workspace = trimr!(workspace::TrimrWorkspace, A, b, c; kwargs...)
workspace = trimr!(workspace::TrimrWorkspace, A, b, c, x0, y0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`trimr`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`TrimrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :trimr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
