```
struct DistributionMeasure <: AbstractMeasure
```

`Distributions.Distribution`を`MeasureBase.AbstractMeasure`としてラップします。

`DistributionMeasure(d::Distribution)`を直接呼び出すことは避けてください。代わりに、特化した`Distribution`から`AbstractMeasure`への変換を可能にするために`AbstractMeasure(d::Distribution)`を使用してください。

`convert(Distribution, m::DistributionMeasure)`または`Distribution(m::DistributionMeasure)`を使用して、`Distribution`に戻すことができます。
