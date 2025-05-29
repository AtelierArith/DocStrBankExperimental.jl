```
MultiIndepMCSampling <: AbstractMultivariateMethod
```

一様モンテカルロサンプリングを使用して、[`MultiMCSampling`](@ref MeasureToolbox.MultiMCSampling)に似た積分を近似する積分評価方法です。ただし、このバリアントは独自のサポートセットを生成し、`MCSample`ラベルの他のすべてのサポートを無視します。これは有限の積分領域に対してのみ有効です。フィールドは含まれていません。
