```
workspace = fgmres!(workspace::FgmresWorkspace, A, b; kwargs...)
workspace = fgmres!(workspace::FgmresWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`fgmres`](@ref)のキーワード引数です。キーワード引数`memory`は唯一の例外です。これは[`fgmres`](@ref)によってのみサポートされており、`FgmresWorkspace`を作成するために必要です。後で変更することはできません。

`workspace`を作成する方法については、[`FgmresWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :fgmres`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
