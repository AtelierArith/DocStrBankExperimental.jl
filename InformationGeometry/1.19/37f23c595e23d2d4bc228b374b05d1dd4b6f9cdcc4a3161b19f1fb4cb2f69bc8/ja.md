```
Exp10Xdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
Exp10Xdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel`またはデータセットオブジェクトを返し、`idxs[i]==true`であるx変数のコンポーネント`i`にexp10が適用されます。データとモデルの両方に対して適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
