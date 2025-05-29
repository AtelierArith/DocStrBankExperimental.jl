```
SqrtXdata(DM::AbstractDataModel) -> AbstractDataModel
SqrtXdata(DS::AbstractDataSet) -> AbstractDataSet
```

データとモデルの両方のx変数に対して平方根が成分ごとに適用された修正された`DataModel`またはデータセットオブジェクトを返します。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
