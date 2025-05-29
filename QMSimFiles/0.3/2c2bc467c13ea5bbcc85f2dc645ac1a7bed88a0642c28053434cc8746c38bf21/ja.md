```
generate_effQTL!(gmap::QMSimMap, af::QMSimAlleleFrequency, dist_or_func, args...; expvar=1.0)
```

アレル頻度 `af` に基づいて QTL 効果を生成および調整し、マップ `gmap` を更新します。QTL 効果を生成するために、分布 `dist`（`Distribution` パッケージで定義）または関数 `func` を提供する必要があります。オプションで引数 `args...` を伴うことができます。生成された効果は、期待される遺伝的分散が `expvar` に等しくなるようにスケーリングされます。この関数は、複数の形質を持つマップファイルをサポートしています。
