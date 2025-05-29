```
resample(udata::UncertainIndexValueDataset, 
    sequential_constraint::SequentialSamplingConstraint,
    grid::InterpolationGrid;
    trunc::TruncateQuantiles = TruncateQuantiles(0.001, 0.999))
```

`udata`の実現を描画し、インデックスに`sequential_constraint`を強制します。次に、実現の値を提供されたインデックスのグリッド（`grid`）に補間します。

非常に大きな補間範囲を避けるために、不確実なインデックスはある大きな分位範囲に切り捨てられます。値は切り捨てられません。  
