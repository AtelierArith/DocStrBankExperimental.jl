```
resample(udata::UncertainIndexValueDataset, 
    grid::InterpolationGrid;
    trunc::TruncateQuantiles = TruncateQuantiles(0.001, 0.999))
```

`udata`の実現を描画し、次にデータ値を`grid`に補間します。

非常に大きな補間範囲を避けるために、不確実なインデックスはかなり大きな分位範囲に切り捨てられます。値は切り捨てられません。
