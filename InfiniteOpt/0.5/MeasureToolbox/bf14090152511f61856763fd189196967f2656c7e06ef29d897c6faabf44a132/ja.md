```
UniIndepMCSampling <: AbstractUnivariateMethod
```

一様モンテカルロサンプリングを使用して積分を近似する積分評価メソッドで、[`UniMCSampling`](@ref MeasureToolbox.UniMCSampling)に似ています。ただし、このバリアントは独自のサポートセットを生成し、`MCSample`ラベルの他のすべてのサポートを無視します。これは有限の積分領域に対してのみ有効です。個別の依存パラメータとは互換性がありません。フィールドは含まれていません。
