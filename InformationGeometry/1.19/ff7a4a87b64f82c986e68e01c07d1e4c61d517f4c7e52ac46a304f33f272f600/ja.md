```
ExpYdata(DM::AbstractDataModel) -> AbstractDataModel
ExpYdata(DS::AbstractDataSet) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを修正して返します。ここで、y変数に対してコンポーネントごとに exp が適用され、データとモデルの両方に対して行われます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
