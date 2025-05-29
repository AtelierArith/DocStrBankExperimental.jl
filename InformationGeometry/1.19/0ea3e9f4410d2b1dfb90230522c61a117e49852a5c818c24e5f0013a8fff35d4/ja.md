```
BiPowerYdata(DM::AbstractDataModel) -> AbstractDataModel
BiPowerYdata(DS::AbstractDataSet) -> AbstractDataSet
```

`DataModel`またはデータセットオブジェクトを返し、ここでBiPowerがy変数に対して成分ごとに適用されます。データとモデルの両方に対して適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
