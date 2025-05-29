```
addtraces!(p::Plot, i::Int, traces::AbstractTrace...)
```

指定された位置にプロットのデータ配列にトレースを追加します。

新しいトレースはインデックス `p.data[i]` から始まります。
