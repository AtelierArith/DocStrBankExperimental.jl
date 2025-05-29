```
Log10Ydata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
Log10Ydata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

指定された変換を通じて線形化された誤差伝播によって不確実性が計算されるとともに、`idxs[i]==true`であるy変数の成分`i`にlog10が適用された修正された`DataModel`またはデータセットオブジェクトを返します。
