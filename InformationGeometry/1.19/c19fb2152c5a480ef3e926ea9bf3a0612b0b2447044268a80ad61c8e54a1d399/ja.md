```
ExpYdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
ExpYdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、`idxs[i]==true` の y-変数のコンポーネント `i` に exp が適用されます。これはデータとモデルの両方に対して行われます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
