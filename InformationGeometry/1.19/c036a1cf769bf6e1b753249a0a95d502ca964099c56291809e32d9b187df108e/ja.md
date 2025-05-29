```
BiRootYdata(DM::AbstractDataModel) -> AbstractDataModel
BiRootYdata(DS::AbstractDataSet) -> AbstractDataSet
```

`DataModel`またはデータセットオブジェクトを返し、ここでBiRootがy変数に対して成分ごとに適用されています。データとモデルの両方においてです。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
