```
batch_particle_data_to_linked_data(translation_dict::Dict, linking_settings::NamedTuple; save_to_csv=true)
```

`particle_data`内のすべての`.csv`ファイルを処理してリンクされた軌道データに変換し、結果を連結します。

全実験配列のリンクされたデータを含む`DataFrame`を返します。これは記録保持とさらなる分析のために[`save_linked_data_with_metadata`](@ref)を使用して`linked_data`に保存されます。

`translation_dict`はファイル名に含まれる情報を詳細に示す辞書です。`linking_settings`はリンクアルゴリズムと顕微鏡情報のための入力パラメータを含みます。これらの引数のうちの1つだけが`FPS`を含むことができます。

詳細な説明については、MicroTrackerの[Linking](@ref)ドキュメントを参照してください。
