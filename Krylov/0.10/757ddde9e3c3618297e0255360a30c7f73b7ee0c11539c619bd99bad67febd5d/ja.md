```
workspace = usymlq!(workspace::UsymlqWorkspace, A, b, c; kwargs...)
workspace = usymlq!(workspace::UsymlqWorkspace, A, b, c, x0; kwargs...)
```

これらの呼び出しでは、`kwargs`は[`usymlq`](@ref)のキーワード引数です。

`workspace`を作成する方法については、[`UsymlqWorkspace`](@ref)を参照してください。

より一般的なインターフェースを使用するには、`method = :usymlq`を指定して[`krylov_workspace`](@ref)を使用してワークスペースを割り当て、[`krylov_solve!`](@ref)を使用してKrylovメソッドをインプレースで実行できます。
