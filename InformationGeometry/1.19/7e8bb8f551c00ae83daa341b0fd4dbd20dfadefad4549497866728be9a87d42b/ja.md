```
SqrtYdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
SqrtYdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、y変数のコンポーネント `i` に対して sqrt が適用され、`idxs[i]==true` の場合、データとモデルの両方で適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
