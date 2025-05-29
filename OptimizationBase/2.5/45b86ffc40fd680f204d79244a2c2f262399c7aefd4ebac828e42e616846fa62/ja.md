```
AutoZygote <: AbstractADType
```

OptimizationFunctionで自動的に未指定の導関数を生成するためのAbstractADTypeの選択肢。使用法：

```julia
OptimizationFunction(f, AutoZygote(); kwargs...)
```

これは[Zygote.jl](https://github.com/FluxML/Zygote.jl)パッケージを使用します。これは、良好な効率でJuliaの大部分を処理する基本的な逆モードADです。ヘッセ行列の構築は、ForwardDiff.jlとZygote.jlを混合した前方-逆方で迅速です。

  * GPUと互換性があります
  * ForwardDiffを介したヘッセ行列ベースの最適化と互換性があります
  * ForwardDiffを介したHvベースの最適化と互換性があります
  * 制約関数とは互換性がありません

未指定の導関数のみが定義されていることに注意してください。たとえば、`OptimizationFunction`に`hess`関数が供給されると、ヘッセ行列はZygoteを介して定義されません。
