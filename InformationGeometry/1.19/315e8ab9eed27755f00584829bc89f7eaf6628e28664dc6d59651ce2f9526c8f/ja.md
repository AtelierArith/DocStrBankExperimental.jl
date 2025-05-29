```
BiPowerYdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
BiPowerYdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、ここで BiPower が y-変数のコンポーネント `i` に適用されます。`idxs[i]==true` の場合、データとモデルの両方で適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
