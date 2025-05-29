```julia
ftypemom(
    mode::MomentMatching.EstimationMode,
    modelname::String
) -> String

```

モデル名に基づいて、[`estimation`](@ref)で一致させるデフォルトのモーメントに対応する文字列を準備します。

モード固有のメソッドが定義されていない場合は、空の文字列がデフォルトとなります。
