```
tea_file(path::AbstractString, value_field_name)
```

`path`で指定されたteaファイルからデータを読み取るノードを取得します。

このteaファイルは、実行時に検証される以下のプロパティを遵守している必要があります：

  * Juliaの`DateTime`と互換性のあるプライマリ時間フィールドを持つこと。
  * `value_field_name`という名前の列が正確に1つだけ存在すること。
  * 時間が*厳密に*増加していること。

ノードの作成時に、ファイルのメタデータセクションが解析され、結果のノードの値の型が推測されます。ただし、データの大部分は評価時にのみ読み取られます。

# 参照

  * [teaファイル仕様](http://discretelogics.com/resources/teafilespec/)
  * [TeaFiles.jl](https://github.com/tpgillam/TeaFiles.jl)

```
