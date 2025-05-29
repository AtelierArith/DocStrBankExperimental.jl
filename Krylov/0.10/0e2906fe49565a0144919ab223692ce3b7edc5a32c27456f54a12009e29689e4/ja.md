```
workspace = cg_lanczos_shift!(workspace::CgLanczosShiftWorkspace, A, b, shifts; kwargs...)
```

この呼び出しでは、`kwargs`は[`cg_lanczos_shift`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CgLanczosShiftWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :cg_lanczos_shift`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
