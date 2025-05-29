```
AutoReverseDiff <: AbstractADType
```

最適化関数で未指定の導関数を自動的に生成するために使用するAbstractADTypeの選択肢。使用法：

```julia
OptimizationFunction(f, AutoReverseDiff(); kwargs...)
```

これは、[ReverseDiff.jl](https://github.com/JuliaDiff/ReverseDiff.jl)パッケージを使用します。`AutoReverseDiff`にはデフォルト引数`compile`があり、逆伝播がコンパイルされるべきかどうかを示します。**`compile`は、`f`に分岐（if文、whileループ）が含まれていない場合にのみ`true`に設定するべきです。そうでないと、誤った導関数を生成する可能性があります！**

`AutoReverseDiff`は一般的に多くの純粋なJuliaコードに適用可能で、`compile=true`の場合、スカラー相互作用が多いコードに対して最も高速なオプションの1つです。ヘッセ行列の計算は、ForwardDiffとReverseDiffを混合して前方-逆方向で行うことで高速です。ただし、`compile=false`の場合、そのパフォーマンスは低下する可能性があります。

  * GPUと互換性がない
  * ForwardDiffと混合することでヘッセ行列ベースの最適化と互換性がある
  * ForwardDiffと混合することでHvベースの最適化と互換性がある
  * 制約関数とは互換性がない

未指定の導関数関数のみが定義されていることに注意してください。たとえば、`OptimizationFunction`に`hess`関数が供給されると、ヘッセ行列はReverseDiffを介して定義されません。

## コンストラクタ

```julia
AutoReverseDiff(; compile = false)
```

#### 注意：現在、コンパイルは定義されていません/使用されていません！
