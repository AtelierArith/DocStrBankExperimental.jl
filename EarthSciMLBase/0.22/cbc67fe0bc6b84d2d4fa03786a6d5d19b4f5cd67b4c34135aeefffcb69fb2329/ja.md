```julia
ConstantWind(t, vals; name)

```

与えられた風速を持つ定常風速モデルコンポーネントを構築します。風速には単位を含める必要があります。例えば、`ConstantWind(t, 1u"m/s", 2u"m/s")`のようにします。
