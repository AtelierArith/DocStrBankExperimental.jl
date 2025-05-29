```
workspace = cg!(workspace::CgWorkspace, A, b; kwargs...)
workspace = cg!(workspace::CgWorkspace, A, b, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`cg`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CgWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :cg`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylov法をインプレースで実行できます。
