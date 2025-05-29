```
workspace = bicgstab!(workspace::BicgstabWorkspace, A, b; kwargs...)
workspace = bicgstab!(workspace::BicgstabWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`bicgstab`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`BicgstabWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :bicgstab`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylov法をインプレースで実行できます。
