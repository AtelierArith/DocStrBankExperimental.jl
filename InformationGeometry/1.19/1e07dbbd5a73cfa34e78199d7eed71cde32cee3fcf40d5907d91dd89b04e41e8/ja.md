```
LogXdata(DM::AbstractDataModel) -> AbstractDataModel
LogXdata(DS::AbstractDataSet) -> AbstractDataSet
```

x変数に対してログがデータとモデルの両方で成分ごとに適用された修正された`DataModel`またはデータセットオブジェクトを返します。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
