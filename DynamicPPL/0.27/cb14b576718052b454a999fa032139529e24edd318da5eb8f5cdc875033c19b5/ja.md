```
LogDensityFunction
```

`model`の対数密度関数を表す呼び出し可能なオブジェクト。

# フィールド

  * `varinfo`: 評価に使用されるvarinfo
  * `model`: 評価に使用されるモデル
  * `context`: 評価に使用されるコンテキスト

# 例

```jldoctest
julia> using Distributions

julia> using DynamicPPL: LogDensityFunction, contextualize

julia> @model function demo(x)
           m ~ Normal()
           x ~ Normal(m, 1)
       end
demo (generic function with 2 methods)

julia> model = demo(1.0);

julia> f = LogDensityFunction(model);

julia> # LogDensityProblems.jlのインターフェースを実装しています。
       using LogDensityProblems

julia> LogDensityProblems.logdensity(f, [0.0])
-2.3378770664093453

julia> LogDensityProblems.dimension(f)
1

julia> # デフォルトでは内部で`VarInfo`を使用しますが、これは必須ではありません。
       f = LogDensityFunction(model, SimpleVarInfo(model));

julia> LogDensityProblems.logdensity(f, [0.0])
-2.3378770664093453

julia> # これも`model`のコンテキストを尊重します。
       f_prior = LogDensityFunction(contextualize(model, DynamicPPL.PriorContext()), VarInfo(model));

julia> LogDensityProblems.logdensity(f_prior, [0.0]) == logpdf(Normal(), 0.0)
true
```
