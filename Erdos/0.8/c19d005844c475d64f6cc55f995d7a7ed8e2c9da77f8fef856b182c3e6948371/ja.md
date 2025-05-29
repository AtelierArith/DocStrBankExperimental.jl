```
readgraph(filename, G=Graph)
readgraph(filename, t, G=Graph; compressed=false)
```

`filename`から形式`t`のグラフを読み込みます。タイプ`G`のグラフまたは対応する有向グラフ/グラフタイプを返します。圧縮ファイルは最終的に読み込むことができます。

サポートされている形式は`:gml, :dot, :graphml, :gexf, :net, :gt`です。

形式が提供されていない場合、`filename`から推測されます。

```
readgraph(s::Symbol, G=Graph)
```

Erdosデータセットコレクションから`s`で識別されるグラフを読み込みます（例：`s=:karate`）。これらはパッケージの`datasets`ディレクトリにある`gt`バイナリ形式で保存されています。利用可能なグラフのリストについては、ドキュメントを参照してください。
