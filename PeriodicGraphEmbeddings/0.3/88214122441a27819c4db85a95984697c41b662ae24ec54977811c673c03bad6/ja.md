```
export_cgd(file, pge::PeriodicGraphEmbedding, name=basename(splitext(file)[1]), append=false)
export_cgd(file, g::PeriodicGraph, name=basename(splitext(file)[1]), append=false)
```

`PeriodicGraph` または `PeriodicGraphEmbedding` を .cgd `file` にエクスポートします（Systre で読み取り可能）。

`append` が設定されている場合、グラフはファイルの末尾に追加されます。
