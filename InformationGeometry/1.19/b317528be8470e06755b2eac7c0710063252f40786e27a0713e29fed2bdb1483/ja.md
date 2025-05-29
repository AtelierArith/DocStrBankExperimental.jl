```
BiPowerXdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
BiPowerXdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、ここで BiPower が x-変数のコンポーネント `i` に適用されます。これは、データとモデルの両方で `idxs[i]==true` の場合です。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
