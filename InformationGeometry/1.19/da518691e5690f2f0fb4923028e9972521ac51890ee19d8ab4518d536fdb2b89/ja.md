```
TransformYdata(DM::AbstractDataModel, Emb::Function, TransformName::String="Trafo") -> AbstractDataModel
TransformYdata(DS::AbstractDataSet, Emb::Function, TransformName::String="Trafo") -> AbstractDataSet
```

y変数が多変数変換`Emb`によってデータとモデルの両方で変換された修正された`DataModel`を返します。ここで、`newmodel(x,θ) = Emb(oldmodel(x,θ))`です。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
