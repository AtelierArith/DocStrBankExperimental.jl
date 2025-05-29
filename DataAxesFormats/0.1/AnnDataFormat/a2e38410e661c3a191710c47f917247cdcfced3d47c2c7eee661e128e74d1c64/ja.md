```
anndata_as_daf(
    adata::Union{AnnData, AbstractString};
    [name::Maybe{AbstractString} = nothing,
    obs_is::Maybe{AbstractString} = nothing,
    var_is::Maybe{AbstractString} = nothing,
    X_is::Maybe{AbstractString} = nothing,
    unsupported_handler::AbnormalHandler = WarnHandler]
)::MemoryDaf
```

`AnnData`を`Daf`データセットとして表示します。具体的には、[`MemoryDaf`](@ref)を使用します。これは行列やベクトルを複製するのではなく、同じものへの参照を含むビューとして機能します。`Daf` APIを使用してビュー内のデータを追加または削除しても、元の`adata`には影響しません。

サポートされていない`AnnData`の注釈は、`unsupported_handler`を使用して処理されます。デフォルトでは、すべてのサポートされていないプロパティについて警告します。

`adata`が文字列の場合、それは自動的に読み込まれる`h5ad`ファイルのパスです。

指定されていない場合、`name`は"名前"の`uns`プロパティの値になります。存在しない場合は、"anndata"になります。

指定されていない場合、`obs_is`（"obs"軸の名前）は"obs_is"の`uns`プロパティの値になります。存在しない場合は、"obs"になります。

指定されていない場合、`var_is`（"var"軸の名前）は"var_is"の`uns`プロパティの値になります。存在しない場合は、"var"になります。

指定されていない場合、`X_is`（"X"行列の名前）は"X_is"の`uns`プロパティの値になります。存在しない場合は、"X"になります。
