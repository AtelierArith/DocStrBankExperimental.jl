```
終了
```

最適化アルゴリズムにおいて、準勾配アルゴリズムで使用される終了基準を指定するためのオプションです。オプションは次のとおりです：

  * [`AfterMaximumIterations`](@ref):  設定された反復回数 ?MaximumIterations に達した後に終了します（デフォルト）。
  * [`AtObjectiveThreshold`](@ref):  参照目的 ?ObjectiveThreshold に達した後に終了します。
  * [`AtGradientThreshold`](@ref):  ゼロ勾配 ?GradientThreshold に達した後に終了します。
