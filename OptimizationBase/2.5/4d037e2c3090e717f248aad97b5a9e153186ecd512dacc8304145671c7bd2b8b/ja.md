```
AutoEnzyme <: AbstractADType
```

OptimizationFunctionで未指定の導関数を自動的に生成するためのAbstractADTypeの選択。使用法：

```julia
OptimizationFunction(f, AutoEnzyme(); kwargs...)
```

これは[Enzyme.jl](https://github.com/EnzymeAD/Enzyme.jl)パッケージを使用します。Enzymeはjuliaから生成されたLLVM IRコードに対して自動微分を行います。非常に効率的で、最適化されたコードに対してADを実行する能力により、Enzymeは最先端のADツールの性能を上回ることができます。

  * GPUと互換性あり
  * ヘッセ行列ベースの最適化と互換性あり
  * Hvベースの最適化と互換性あり
  * 制約と互換性あり

未指定の導関数のみが定義されていることに注意してください。たとえば、`OptimizationFunction`に`hess`関数が供給されると、ヘッセ行列はEnzymeを介して定義されません。
