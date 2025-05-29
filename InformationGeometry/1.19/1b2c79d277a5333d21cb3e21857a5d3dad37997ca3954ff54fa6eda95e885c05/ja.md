```
Log10Ydata(DM::AbstractDataModel) -> AbstractDataModel
Log10Ydata(DS::AbstractDataSet) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、y変数に対してデータとモデルの両方でコンポーネントごとに log10 が適用されます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
