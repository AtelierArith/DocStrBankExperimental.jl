```
read_data_list(path_to_data_or_list::String)
```

フィリップスのMRシステムから *.{data,list} ファイルを読み込むための主要なエントリポイントです。

この関数はデータを実際に*読み込む*だけで、例えばk空間にソートすることはありません。

# 引数

  * `path_to_data_or_list::String`: データおよびリストファイルへのパス（拡張子なし）。
  * `remove_empty_fields::Bool=true`: trueの場合、サンプルがないフィールドを削除します。

# 戻り値

  * `samples_per_type::NamedTuple`: 各フィールドが「複素データベクトル」のタイプの1つに対応するサンプルの配列であるNamedTuple。
  * `attributes_per_type::NamedTuple`: 各フィールドが「複素データベクトル」のタイプの1つに対応する属性を含むDataFrameであるNamedTuple。
  * `info::Vector{String}`: スキャンに関する一般的な情報。

# 注意事項

.dataおよび.listファイルは同じ名前である必要があります（拡張子を除く）。この関数は、パスに.dataおよび.listを追加してそれぞれのファイルを読み込むため、パスに拡張子を持つ必要はありません。
