```
BiRootXdata(DM::AbstractDataModel) -> AbstractDataModel
BiRootXdata(DS::AbstractDataSet) -> AbstractDataSet
```

BiRootがデータとモデルの両方のx変数にコンポーネント単位で適用された修正された`DataModel`またはデータセットオブジェクトを返します。 不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
