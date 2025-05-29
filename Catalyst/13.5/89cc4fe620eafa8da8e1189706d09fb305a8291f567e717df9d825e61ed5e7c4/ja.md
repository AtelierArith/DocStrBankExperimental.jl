```
savegraph(g::Graph, fname, fmt="png")
```

[`Graph`](@ref)によって生成された`Graph`を、名前`fname`と拡張子`fmt`のファイルに保存します。

注意:

  * `fmt="png"`はデフォルトの出力形式です。
  * Graphviz jllがインストールされているか、Graphvizがインストールされていてコマンドラインからアクセス可能である必要があります。
