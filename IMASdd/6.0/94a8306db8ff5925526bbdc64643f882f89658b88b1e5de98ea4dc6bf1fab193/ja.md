```
imas2hdf(@nospecialize(ids::Union{IDS,IDSvector}), filename::AbstractString;
         mode::String="w", target_group::String="/", overwrite::Bool=false,
         freeze::Bool=false, strict::Bool=false, desc::String="", kw...)
```

IMASデータ構造をOMAS HDF5ファイルに保存します。

引数:

  * `filename`: HDF5ファイルのパス
  * `mode`: ファイルオープンモード ("w", "a", または "r+"); "a"は "r+"に変換されます
  * `target_group`: データが保存されるグループ (デフォルトは `"/"`)
  * `overwrite`: trueの場合、ターゲットグループが存在する場合は上書きします
  * `show_warnings`: trueの場合、警告メッセージを表示します
  * `freeze` は式を評価します
  * `strict` はITER IMASのみに厳密に存在するフィールドをダンプします
  * `desc`: 追加情報の説明 (例: ショット番号)
  * `compress`: 圧縮レベル、0（圧縮なし）から9（最高）までの整数
  * `kw...`: 内部ディスパッチに渡されるオプション

戻り値:

`imas2hdf(ids, gparent; freeze, strict, desc)`の結果。
