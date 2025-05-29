```
writegraph(file, g)
writegraph(file, g, t; compress=false)
```

グラフ `g` を `file` にフォーマット `t` で保存します。

最終的に、結果のファイルはgzipフォーマットで圧縮される可能性があります。

現在サポートされているフォーマットは `:gml, :graphml, :gexf, :dot, :net, :gt` です。

フォーマットが指定されていない場合、圧縮とともに `file` から推測されます。
