```
SWGFormat
```

SimpleWeightedGraphファイルのストレージフォーマット。1つのファイルに複数のグラフが含まれる場合があります。

各グラフについて、ファイルには1行のヘッダーが含まれています：

```
"LightGraphs.SimpleWeightedGraph", <num_vertices>, <num_edges>, {"d" | "u"}, <name>[, <ver>, <vdatatype>, <wdatatype>, <graphcode>]
```

  * `"LightGraphs.SimpleWeightedGraph"` は固定文字列です
  * `<num_vertices>` は整数です
  * `<num_edges>` は整数です
  * `"d"` は有向グラフ、`"u"` は無向グラフ（このオプションは追加のエッジ構築を行わず、正しいタイプのグラフを返すためにのみ使用されます）
  * `<name>` は文字列です
  * `<ver>` は整数です
  * `<vdatatype>` は文字列です（"UInt8" など）
  * `<wdatatype>` は重みのデータ型を説明する文字列です
  * `<graphcode>` は文字列です。

ヘッダーの後には、各エッジのリスト（カンマ区切り）があり、それぞれが別の行にあります：

```
<src>,<dst>,<weight>
```

  * `<src>` はエッジのソースを示す整数です
  * `<dst>` はエッジの宛先を示す整数です
  * `<weight>` はエッジの重みを示す実数です
