```
LogYdata(DM::AbstractDataModel) -> AbstractDataModel
LogYdata(DS::AbstractDataSet) -> AbstractDataSet
```

y変数に対して、データとモデルの両方で成分ごとに対数が適用された修正された`DataModel`またはデータセットオブジェクトを返します。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
