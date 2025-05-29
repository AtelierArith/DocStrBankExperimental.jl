```
add_info_columns_from_filename(particle_data::AbstractDataFrame, translation_dict::AbstractDict)
```

`filename` 列から実験メタデータを抽出し、`particle_data` にそれぞれの新しい列を作成します。新しい `DataFrame` を返します。

ファイル名はアンダースコアで区切られ、ピリオドは `p` で示されていると仮定します。`translation_dict` はファイル名の形式を詳述しています。詳細な説明については、MicroTracker ドキュメントを参照してください: [Translation Dictionary](@ref).
