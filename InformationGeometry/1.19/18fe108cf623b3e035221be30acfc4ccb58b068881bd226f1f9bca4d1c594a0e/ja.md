```
BiRootXdata(DM::AbstractDataModel, idxs::BoolVector) -> AbstractDataModel
BiRootXdata(DS::AbstractDataSet, idxs::BoolVector) -> AbstractDataSet
```

`DataModel` またはデータセットオブジェクトを返し、`idxs[i]==true` の x-変数のコンポーネントに BiRoot が適用されます。これはデータとモデルの両方において行われます。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
