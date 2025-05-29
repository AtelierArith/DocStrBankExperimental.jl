```
multiscale(algorithm::MultiScaleAlgorithm, [args...], x)
```

任意の [`InformationMeasureEstimator`](@ref) または [`ComplexityEstimator`](@ref) のマルチスケールバージョンを計算するための便利な関数です。

`multiscale` の戻り値の型は、`Vector{Real}` または `Vector{Vector{Real}}` のいずれかであり、以下の利用可能な粗粒化手法を参照してください。

これは、与えられた `algorithm` を使用して [`downsample`](@ref) を利用し、まず `algorithm.scales` のスケールファクターに対して `x` の粗粒化されたダウンサンプル版を生成します。その後、入力引数に応じて、各粗粒化された時系列に [`information`](@ref) または [`complexity`](@ref) が適用されます。もし `N = length(x)` であれば、`x` の最も厳しくダウンサンプルされたバージョンの長さは `N ÷ maximum(algorithm.scales)` であり、スケールファクターが `1` の場合は元の時系列が考慮されます。

## 説明

この関数は、[Costa2002](@cite) のマルチスケールエントロピーを任意の離散情報量、任意の微分情報量、およびその他の複雑さの尺度に一般化します。

## 粗粒化アルゴリズム

利用可能なダウンサンプリングルーチンは次のとおりです：

  * [`RegularDownsampling`](@ref) は、スケールごとに単一の `Vector` を生成します。
  * [`CompositeDownsampling`](@ref) は、スケールごとに `Vector{Vector}` を生成します。

## 例

`multiscale` は、任意の離散または微分情報量推定器と共に使用できます。例えば、マルチスケールのツァリスエントロピーを計算する2つの方法を示します：

```julia
using ComplexityMeasures
x = randn(1000)
downsampling = RegularDownsampling(scales = 1:5) # マルチスケールアルゴリズム

# ベイジアン正則化を用いた象徴的（順序パターンベースの）確率推定、
# エントロピーのジャックナイフ推定。
o = OrdinalPatterns{3}(2) # 結果空間
probest = BayesianRegularization() # 確率推定器
hest = Jackknife(Tsallis(q = 1.5)) # エントロピー推定器
multiscale(downsampling, hest, probest, o, x)

# 微分kNNベースの推定器：
hest = LeonenkoProzantoSavani(Tsallis(q = 1.5), k = 10) # 10近傍
multiscale(downsampling, hest, x)
```

任意の [`ComplexityEstimator`](@ref) のマルチスケールバリアントも簡単に計算できます。第二次モーメントを使用して「一般化されたマルチスケールサンプルエントロピー [Costa2015](@cite)」を計算してみましょう。

```julia
using ComplexityMeasures, Statistics
multiscale(CompositeDownsampling(; f = Statistics.var), SampleEntropy(x), x)
```
