```
information([die::DiscreteInfoEstimator,] [est::ProbabilitiesEstimator,] o::OutcomeSpace, x) → h::Real
information(o::OutcomeSpace, x) → h::Real
```

入力データ `x` から、提供された [`DiscreteInfoEstimator`](@ref) と [`ProbabilitiesEstimator`](@ref) を使用して、指定された [`OutcomeSpace`](@ref) に対して離散情報量を推定します。

代わりに、最初の引数（`die`）に [`InformationMeasure`](@ref) を提供することもでき、情報推定のためにデフォルトで [`PlugIn`](@ref) 推定が使用されます。最初の引数（`die`）を省略することもでき、その場合は `Shannon()` が使用されます。第二の引数（`est`）を省略することもでき、その場合はデフォルトで [`RelativeAmount`](@ref) 確率推定器が使用されます。一部の情報量推定器（例: [`GeneralizedSchuermann`](@ref)）はカウントに直接作用し、したがって `est` を無視します。

```
information([e::DiscreteInfoEstimator,] p::Probabilities) → h::Real
information([e::DiscreteInfoEstimator,] c::Counts) → h::Real
```

上記と同様ですが、事前に計算された [`Probabilities`](@ref) `p` または [`Counts`](@ref) から情報量を推定します。カウントは [`RelativeAmount`](@ref) を使用して確率に変換されますが、推定器 `e` がカウントを直接使用する場合はこの限りではありません。

参照: [`information_maximum`](@ref)、[`information_normalized`](@ref) の正規化バージョン。

## 例（単純推定）

離散量を推定する最も簡単な方法は、[`InformationMeasure`](@ref) を直接提供し、[`OutcomeSpace`](@ref) と組み合わせることです。これにより、量のために「単純な」[`PlugIn`](@ref) 推定器が使用され、確率のために「単純な」[`RelativeAmount`](@ref) 推定器が使用されます。

```julia
x = randn(100) # 一部の入力データ
o = ValueBinning(RectangularBinning(5)) # 5ビンのヒストグラムの結果空間
h_s = information(Shannon(), o, x)
```

以下はさらにいくつかの例です：

```julia
x = [rand(Bool) for _ in 1:10000] # コイントス
ps = probabilities(x) # 定義により約 [0.5, 0.5] を返す
h = information(ps) # 定義により約 1 ビットを返す（デフォルトでシャノンエントロピー）
h = information(Shannon(), ps) # 上記と構文的に同等
h = information(Shannon(), UniqueElements(), x) # 上記と構文的に同等
h = information(Renyi(2.0), ps) # コイントスに対しては順序 `q` は関係ないため、1 を返す
h = information(OrdinalPatterns(;m=3), x) # 定義により約 2 を返す
```

## 例（バイアス補正推定）

情報量の推定に対する [`PlugIn`](@ref) 推定と確率に対する [`RelativeAmount`](@ref) 推定はバイアスがあることが知られています。科学文献には、このバイアスを補正する推定器が豊富に存在し、量の推定レベルと確率の推定レベルの両方で利用可能です。したがって、改善された推定のために任意の [`DiscreteInfoEstimator`](@ref) と任意の [`ProbabilitiesEstimator`](@ref) を組み合わせて使用するオプションを提供します。カスタム確率推定器は、カウント互換の [`OutcomeSpace`](@ref) でのみ機能することに注意してください。

```julia
x = randn(100)
o = ValueBinning(RectangularBinning(5))

# 様々な専用推定器を使用してシャノンエントロピー推定を行う
h_s = information(MillerMadow(Shannon()), RelativeAmount(), o, x)
h_s = information(HorvitzThompson(Shannon()), Shrinkage(), o, x)
h_s = information(Schuermann(Shannon()), Shrinkage(), o, x)

# 一般的な `Jackknife` 推定器を使用して情報量を推定
h_r = information(Jackknife(Renyi()), Shrinkage(), o, x)
j_t = information(Jackknife(TsallisExtropy()), BayesianRegularization(), o, x)
j_r = information(Jackknife(RenyiExtropy()), RelativeAmount(), o, x)
```
