```
BandedMatrix(kv::Pair{<:Integer,<:AbstractVector}...)
```

対角線とベクトルの `Pair` から正方行列を構築します。ベクトル `kv.second` は `kv.first` 対角線に配置されます。
