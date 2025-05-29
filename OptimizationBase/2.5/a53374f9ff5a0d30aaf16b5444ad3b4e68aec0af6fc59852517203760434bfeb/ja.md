```
AutoForwardDiff{chunksize} <: AbstractADType
```

最適化関数で未指定の導関数関数を自動的に生成するための AbstractADType の選択肢。使用法：

```julia
OptimizationFunction(f, AutoForwardDiff(); kwargs...)
```

これは [ForwardDiff.jl](https://github.com/JuliaDiff/ForwardDiff.jl) パッケージを使用します。特に重いスカラー相互作用を持つ小さなシステムに対して最も高速な選択肢です。使いやすく、緩い型制約を持つほとんどの Julia 関数と互換性があります。ただし、前方モードであるため、他の AD 選択肢と比較してスケーラビリティが悪いです。ヘッセ行列の構築は、前方-前方アプローチを使用するため最適ではありません。

  * GPU と互換性あり
  * ヘッセ行列ベースの最適化と互換性あり
  * Hv ベースの最適化と互換性あり
  * 制約と互換性あり

未指定の導関数関数のみが定義されていることに注意してください。たとえば、`OptimizationFunction` に `hess` 関数が供給されると、ヘッセ行列は ForwardDiff を介して定義されません。
