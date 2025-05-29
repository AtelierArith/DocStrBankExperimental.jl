```
AutoTracker <: AbstractADType
```

OptimizationFunctionで未指定の導関数を自動的に生成するためのAbstractADTypeの選択。使用法：

```julia
OptimizationFunction(f, AutoTracker(); kwargs...)
```

これは[Tracker.jl](https://github.com/FluxML/Tracker.jl)パッケージを使用します。一般的にReverseDiffよりも遅いですが、多くの純粋なJuliaコードに一般的に適用可能です。

  * GPUと互換性あり
  * ヘッセ行列ベースの最適化とは互換性なし
  * Hvベースの最適化とは互換性なし
  * 制約関数とは互換性なし

未指定の導関数のみが定義されていることに注意してください。たとえば、`OptimizationFunction`に`hess`関数が供給されると、ヘッセ行列はTrackerを介して定義されません。
