```
readnetwork(filename, G=Network)
readnetwork(filename, t, G=Network; compressed=false)
```

`filename`から`t`形式のネットワークを読み込みます。タイプ`G`のネットワーク（必要に応じて対応する有向/無向タイプ）を返します。圧縮ファイルも最終的に読み込むことができます。

サポートされている形式は`:gml, :dot, :graphml, :gexf, :net, :gt`です。可能な場合、グラフ、エッジ、および頂点のプロパティも読み込まれます。

形式が提供されていない場合、`filename`から推測されます。

```
readnetwork(s::Symbol, G=Network)
```

Erdosのデータセットコレクションから`s`で識別されるネットワークを読み込みます（例：`s=:karate`）。これらはパッケージの`datasets`ディレクトリにある`gt`バイナリ形式で保存されています。利用可能なグラフのリストについては、ドキュメントを参照してください。
