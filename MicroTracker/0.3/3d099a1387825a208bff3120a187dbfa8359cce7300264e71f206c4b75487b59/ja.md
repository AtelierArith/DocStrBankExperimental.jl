```
particle_data_to_linked_data(video_name::AbstractString, translation_dict::Dict, linking_settings::NamedTuple)
```

粒子データをリンクされた軌道データに処理し、瞬時の速度やその他の重要なデータを計算します。`DataFrame`を返し、その後[`save_linked_data_with_metadata`](@ref)を使用して`linked_data`に保存できます。

`video_name`に対応する粒子データのcsvが`particle_data`フォルダーに存在する必要があります。`translation_dict`は、ファイル名に含まれる情報を詳述した辞書です。詳細については、MicroTrackerのドキュメントを参照してください（参照が必要）。
