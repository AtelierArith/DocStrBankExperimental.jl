```
SqrtYdata(DM::AbstractDataModel) -> AbstractDataModel
SqrtYdata(DS::AbstractDataSet) -> AbstractDataSet
```

y変数に平方根が成分ごとに適用された修正された`DataModel`またはデータセットオブジェクトを返します。これはデータとモデルの両方に適用されます。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
