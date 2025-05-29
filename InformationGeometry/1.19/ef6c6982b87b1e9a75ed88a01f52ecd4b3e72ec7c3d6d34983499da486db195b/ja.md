```
TransformXdata(DM::AbstractDataModel, Emb::Function, iEmb::Function, TransformName::String="Trafo") -> AbstractDataModel
TransformXdata(DS::AbstractDataSet, Emb::Function, TransformName::String="Trafo") -> AbstractDataSet
```

`DataModel`を修正したものを返します。ここで、x変数は、データとモデルの両方で多変数変換`Emb`によって変換されています。モデルは`newmodel(x,θ) = oldmodel(Emb(x),θ)`で表されます。`iEmb`は`Emb`の逆を示します。不確実性は、与えられた変換を通じて線形化された誤差伝播によって計算されます。
