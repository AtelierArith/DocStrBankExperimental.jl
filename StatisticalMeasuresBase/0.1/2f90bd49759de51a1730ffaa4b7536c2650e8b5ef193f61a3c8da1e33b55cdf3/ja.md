```
measurements(measure, ŷ, y[, weights, class_weights::AbstractDict])
```

`y`の各観測値に対して1つの測定値を返し、単一の集約測定値ではありません。それ以外は、データに対してmeasureを直接呼び出すのと同じ動作です。

# 新しい実装

新しい測定タイプのためにこの関数をオーバーロードすることは任意です。フォールバックは、集約測定を返し、それを`n`回繰り返します。ここで、`n = MLUtils.numobs(y)`（`numobs`が実装されていない場合は`length(y)`にフォールバックします）。ラップされた測定のために`measurements`をオーバーロードする必要は通常ありません。すべての[`multimeasure`](@ref)sは明らかなフォールバックを提供し、他のラッパーは単に原子測定の`measurements`メソッドを転送します。オーバーロードする場合は、次のシグネチャを使用してください。

```
StatisticalMeasuresBase.measurements(measure::SomeMeasureType, ŷ, y)
StatisticalMeasuresBase.measurements(measure::SomeMeasureType, ŷ, weights)
StatisticalMeasuresBase.measurements(measure::SomeMeasureType, ŷ, class_weights::AbstractDict)
StatisticalMeasuresBase.measurements(measure::SomeMeasureType, ŷ, weights, class_weights)
```
