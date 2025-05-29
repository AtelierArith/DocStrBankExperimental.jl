```
daf_as_anndata(
    daf::DafReader;
    [obs_is::Maybe{AbstractString} = nothing,
    var_is::Maybe{AbstractString} = nothing,
    X_is::Maybe{AbstractString} = nothing,
    h5ad::Maybe{AbstractString} = nothing]
)::AnnData
```

`daf` データセットを `AnnData` として表示します。これは行列やベクトルを複製するのではなく、同じものへの参照を含むビューとして機能します。`AnnData` APIを使用してビュー内でデータを追加または削除しても、元の `daf` データセットには影響しません。

指定されている場合、結果は `h5ad` ファイルにも書き込まれます。

指定されていない場合、`obs_is`（"obs" 軸の名前）は、存在する場合は "obs_is" スカラープロパティの値になります。そうでなければ、"obs" になります。

指定されていない場合、`var_is`（"var" 軸の名前）は、存在する場合は "var_is" スカラープロパティの値になります。そうでなければ、"var" になります。

指定されていない場合、`X_is`（"X" 行列の名前）は、存在する場合は "X_is" スカラープロパティの値になります。そうでなければ、"X" になります。

最終的な `obs_is`、`var_is`、`X_is` の各値は、デフォルト値（"obs"、"var"、"X"）が使用されない限り、非構造的な注釈として保存されます。

選択された "obs" および "var" 軸のすべてのスカラープロパティ、ベクトルプロパティ、およびこれらの軸の行列プロパティは、返される新しい `AnnData` オブジェクトに保存されます。
