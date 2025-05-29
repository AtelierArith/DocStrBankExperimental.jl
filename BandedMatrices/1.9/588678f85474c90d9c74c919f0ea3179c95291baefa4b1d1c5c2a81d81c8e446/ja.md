```
BandedMatrix{T}(kv::Pair, (m,n), (l,u))
```

バンド幅 (l,u) を持つ m × n BandedMatrix を対角線とベクトルの `Pair` から構築します。ベクトル `kv.second` は `kv.first` 対角線に配置されます。
