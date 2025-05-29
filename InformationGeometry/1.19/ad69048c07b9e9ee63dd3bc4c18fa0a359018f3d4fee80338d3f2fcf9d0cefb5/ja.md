```
Log10Xdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
Log10Xdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、`idxs[i]==true` の場合に x-変数のコンポーネント `i` に log10 が適用されます。データとモデルの両方に対して適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
