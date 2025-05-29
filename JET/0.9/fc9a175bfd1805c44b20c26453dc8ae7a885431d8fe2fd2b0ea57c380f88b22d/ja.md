```
reportkey(report::InferenceErrorReport)
```

`report`のランタイムディスパッチ呼び出しサイトの識別子を返します。

分析するレポートの長いリストがある場合、`urpts = unique(reportkey, rpts)`は、異なるエントリポイントから同じランタイムディスパッチに到達する「重複」を削除するかもしれません。
