```
makeWaveletGrid!(tsg::TasmanianSG; order=1, level_limits=Vector{Int32}(undef, 0))
```

は、`tsg`によって保持されている既存のグリッドを破棄し、ウェーブレットルールを使用して新しいスパースグリッドを作成します。

order: Int (1または3でなければならない)        実装されているのは、オーダー1および3のウェーブレットのみです。
