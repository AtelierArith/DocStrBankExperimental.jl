```
workspace = gpmr!(workspace::GpmrWorkspace, A, B, b, c; kwargs...)
workspace = gpmr!(workspace::GpmrWorkspace, A, B, b, c, x0, y0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`gpmr`](@ref)のキーワード引数です。キーワード引数`memory`は唯一の例外です。これは[`gpmr`](@ref)によってのみサポートされており、`GpmrWorkspace`を作成するために必要です。後で変更することはできません。

`workspace`を作成する方法については、[`GpmrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :gpmr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してクリロフ法をインプレースで実行できます。
