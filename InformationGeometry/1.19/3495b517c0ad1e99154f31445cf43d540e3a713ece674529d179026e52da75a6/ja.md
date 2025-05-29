```
BiExpYdata(DM::AbstractDataModel) -> AbstractDataModel
BiExpYdata(DS::AbstractDataSet) -> AbstractDataSet
```

`DataModel`またはデータセットオブジェクトを返し、ここでBiExpがデータ内のy変数とモデルの両方に対して成分ごとに適用されます。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
