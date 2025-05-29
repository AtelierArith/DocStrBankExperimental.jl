```
AutoFiniteDiff{T1,T2,T3} <: AbstractADType
```

OptimizationFunctionで自動的に未指定の導関数を生成するためのAbstractADTypeの選択。使用法：

```julia
OptimizationFunction(f, AutoFiniteDiff(); kwargs...)
```

これは[FiniteDiff.jl](https://github.com/JuliaDiff/FiniteDiff.jl)を使用します。必ずしも最も効率的ではありませんが、`f`関数が自動微分可能である必要がない唯一の選択肢であり、これは任意の選択肢に適用されます。ただし、有限差分を使用しているため、この手法は導関数の推定に数値誤差を導入するため注意が必要です。

  * GPUと互換性あり
  * ヘッセ行列ベースの最適化と互換性あり
  * Hvベースの最適化と互換性あり
  * 制約関数と互換性あり

未指定の導関数のみが定義されていることに注意してください。たとえば、`OptimizationFunction`に`hess`関数が供給されると、ヘッセ行列はFiniteDiffを介して定義されません。

## コンストラクタ

```julia
AutoFiniteDiff(; fdtype = Val(:forward)fdjtype = fdtype, fdhtype = Val(:hcentral))
```

  * `fdtype`: 勾配を定義するために使用される方法
  * `fdjtype`: 制約のヤコビアンを定義するために使用される方法
  * `fdhtype`: ヘッセ行列を定義するために使用される方法

導関数タイプ指定子に関する詳細は、[FiniteDiff.jlのドキュメント](https://github.com/JuliaDiff/FiniteDiff.jl)を参照してください。
