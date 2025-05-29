```
Log10Xdata(DM::AbstractDataModel) -> AbstractDataModel
Log10Xdata(DS::AbstractDataSet) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを修正して返し、データとモデルの両方の x 変数に対して成分ごとに log10 が適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
