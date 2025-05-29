```
LogYdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
LogYdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、`idxs[i]==true` の y-変数のコンポーネント `i` に対してログが適用されます。データとモデルの両方で適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
