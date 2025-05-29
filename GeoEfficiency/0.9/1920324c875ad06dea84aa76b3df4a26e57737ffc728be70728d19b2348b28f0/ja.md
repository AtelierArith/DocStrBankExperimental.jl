```
typeofSrc(x::Int)::SrcType
```

グローバル `GeoEfficiency.srcType` の値を `x` に対応して設定し、返します。

  * srcUnknown = -1 および任意の負の整数はそのように扱われます、
  * srcPoint   = 0,
  * srcLine    = 1,
  * srcDisk    = 2,
  * srcVolume  = 3,
  * srcNotPoint = 4 および4より大きい任意の整数はそのように扱われます。
