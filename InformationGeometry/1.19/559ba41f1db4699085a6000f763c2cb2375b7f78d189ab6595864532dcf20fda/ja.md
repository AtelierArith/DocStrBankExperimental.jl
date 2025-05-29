```
WaterfallPlot(R::MultistartResults; BiLog::Bool=true, MaxValue::Real=3000, StepTol::Real=1e-3, kwargs...)
```

与えられたMultistartFitの結果に対してウォーターフォールプロットを表示します。`StepTol`は、ウォーターフォールプロット内の隣接する2つの値の差がステップを構成するかどうかを決定するために使用されます。`StepTol=0`はステップマークを無効にします。`MaxValue`は、最適化後のコスト関数が最良の最適解と比較して大きすぎる点を無視するための閾値を設定するために使用されます。`DoBiLog=false`はコスト関数の対数スケールを無効にします。
