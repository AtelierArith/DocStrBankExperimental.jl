```
abstract type PrimitiveMeasure <: AbstractMeasure end
```

MeasureTheoryエコシステムにおいて、*primitive* measureは、その定義と構築が他の測度に依存しない測度です。Primitive measuresは以下の法則を満たします：

```
basemeasure(μ::PrimitiveMeasure) = μ

logdensity_def(μ::PrimitiveMeasure, x) = 0.0

logdensity_def(μ::M, ν::M, x) where {M<:PrimitiveMeasure} = 0.0
```
