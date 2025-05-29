```
Exp10Ydata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
Exp10Ydata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel`またはデータセットオブジェクトを返し、`idxs[i]==true`であるy変数のコンポーネント`i`にexp10が適用されます。データとモデルの両方で適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
