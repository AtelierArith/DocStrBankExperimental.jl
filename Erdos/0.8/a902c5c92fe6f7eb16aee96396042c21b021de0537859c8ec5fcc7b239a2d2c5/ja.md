```
writenetwork(file, g)
writenetwork(file, g, t; compress=false)
```

ネットワーク `g` を `file` にフォーマット `t` で保存します。

最終的に、結果のファイルは gzip 形式で圧縮される可能性があります。

現在サポートされているフォーマットは `:gml, :graphml, :gexf, :dot, :net, :gt` です。可能な場合、グラフ、エッジ、および頂点のプロパティも書き込まれます。

フォーマットが提供されていない場合、ファイルから圧縮とともに推測されます。
