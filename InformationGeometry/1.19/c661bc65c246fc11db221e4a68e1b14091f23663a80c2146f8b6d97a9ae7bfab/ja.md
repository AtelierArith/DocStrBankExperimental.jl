```
Exp10Ydata(DM::AbstractDataModel) -> AbstractDataModel
Exp10Ydata(DS::AbstractDataSet) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、ここで exp10 がデータ内の y 変数とモデルの両方に対して成分ごとに適用されます。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
