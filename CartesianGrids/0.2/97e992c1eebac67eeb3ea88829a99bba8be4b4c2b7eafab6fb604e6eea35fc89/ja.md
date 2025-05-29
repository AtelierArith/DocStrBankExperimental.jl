```
tensorproduct!(q::EdgeGradient,u::Edges,v::Edges,ut::EdgeGradient,vt::EdgeGradient)
```

`u` と `v` のインプレーステンソル積を計算し、結果を `q` に返します。`ut` と `vt` は一時的なストレージとして提供されます。
