```
workspace = craig!(workspace::CraigWorkspace, A, b; kwargs...)
```

この呼び出しでは、`kwargs`は[`craig`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CraigWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :craig`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylov法をインプレースで実行できます。
