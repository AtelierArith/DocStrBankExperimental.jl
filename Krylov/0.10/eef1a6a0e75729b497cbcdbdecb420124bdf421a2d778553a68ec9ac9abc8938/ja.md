```
workspace = dqgmres!(workspace::DqgmresWorkspace, A, b; kwargs...)
workspace = dqgmres!(workspace::DqgmresWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`dqgmres`](@ref)のキーワード引数です。キーワード引数`memory`は唯一の例外です。これは[`dqgmres`](@ref)によってのみサポートされており、`DqgmresWorkspace`を作成するために必要です。後で変更することはできません。

`workspace`を作成する方法については、[`DqgmresWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :dqgmres`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してクリロフ法をインプレースで実行できます。
