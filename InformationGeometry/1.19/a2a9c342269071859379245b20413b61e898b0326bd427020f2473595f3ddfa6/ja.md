```
Exp10Xdata(DM::AbstractDataModel) -> AbstractDataModel
Exp10Xdata(DS::AbstractDataSet) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、ここで exp10 がデータ内の x 変数とモデルの両方に成分ごとに適用されます。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
