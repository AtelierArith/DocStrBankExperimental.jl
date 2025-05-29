```
workspace = lsmr!(workspace::LsmrWorkspace, A, b; kwargs...)
```

この呼び出しでは、`kwargs`は[`lsmr`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`LsmrWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :lsmr`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylov法をインプレースで実行できます。
