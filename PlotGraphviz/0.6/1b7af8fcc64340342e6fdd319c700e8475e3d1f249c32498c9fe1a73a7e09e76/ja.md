```
read_dot_file(file)
```

DOT形式からグラフをインポートし、ファイル`SimpleWeightedGraph`または`SimpleWeightedDiGraph`に保存します。グラフレイアウトのためのAttributeDictを返します。ToDo: 適切なDOTファイルでない場合のエラーハンドリングは実装されていません。

#### 引数

  * `file::AbstractString`: dotファイルのファイル名（例："graph.dot"）
