```
workspace = cgls_lanczos_shift!(workspace::CglsLanczosShiftWorkspace, A, b, shifts; kwargs...)
```

この呼び出しでは、`kwargs`は[`cgls_lanczos_shift`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`CglsLanczosShiftWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :cgls_lanczos_shift`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
