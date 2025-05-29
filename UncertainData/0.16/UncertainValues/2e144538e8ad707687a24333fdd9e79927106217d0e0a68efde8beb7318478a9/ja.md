```
UncertainValue(distribution::Type{D}, a::T1, b::T2;
    kwargs...) where {T1<:Number, T2 <: Number, D<:Distribution}
```

# 二項パラメータ分布のコンストラクタ

`UncertainValue`は現在、以下の二項パラメータ分布に対して実装されています: `Uniform`, `Normal`, `Binomial`, `Beta`, `BetaPrime`, `Gamma`, および `Frechet`。

### 引数

  * **`a`, `b`**: `distribution`によって異なる意味を持つ一般的なパラメータ。以下のリストを参照してください。
  * **`distribution`**: `Distributions.jl`からの有効な一変量分布。

正確に`a`と`b`が何であるかは、提供される分布によって異なります。

  * `UncertainValue(Normal, μ, σ)`は`UncertainScalarNormallyDistributed`インスタンスを返します。
  * `UncertainValue(Uniform, lower, upper)`は`UncertainScalarUniformlyDistributed`インスタンスを返します。
  * `UncertainValue(Beta, α, β)`は`UncertainScalarBetaDistributed`インスタンスを返します。
  * `UncertainValue(BetaPrime, α, β)`は`UncertainScalarBetaPrimeDistributed`インスタンスを返します。
  * `UncertainValue(Gamma, α, θ)`は`UncertainScalarGammaDistributed`インスタンスを返します。
  * `UncertainValue(Frechet, α, θ)`は`UncertainScalarFrechetDistributed`インスタンスを返します。
  * `UncertainValue(Binomial, n, p)`は`UncertainScalarBinomialDistributed`インスタンスを返します。

### キーワード引数

  * **`nσ`**: `distribution <: Distributions.Normal`の場合、`lower`と`upper`（すなわち両方、なぜならそれらは`μ`から同じ距離にあるため）が`μ`から何標準偏差離れているかを示します。
  * **`tolerance`**: 正規分布の構築を許可するために不確実性がどれだけ対称でなければならないかを決定する閾値（`upper - lower > threshold`が必要です）。
  * **`trunc_lower`**: 無限サポートを持つ分布の下限切断境界。デフォルトは`-Inf`です。
  * **`trunc_upper`**: 無限サポートを持つ分布の上限切断境界。デフォルトは`Inf`です。

## 例

### 正規分布

正規分布は、コンストラクタ`UncertainValue(μ, σ, Normal; kwargs...)`を使用して形成されます。これにより、平均μおよび標準偏差σ/nσの正規分布が得られます（nσはキーワード引数として指定する必要があります）。

```julia
# 平均 = 2.3、標準偏差 = 0.3の正規分布。
UncertainValue(2.3, 0.3, Normal)

# 平均 = 2.3、標準偏差 = 0.3/2の正規分布。
UncertainValue(2.3, 0.3, Normal, nσ = 2)

# 平均 = 2.3、標準偏差 = 0.3の正規分布で、区間`[1, 3]`に切断されています。
UncertainValue(2.3, 0.3, Normal, trunc_lower = 1.0, trunc_upper = 3.0)
```

### 一様分布

一様分布は、`UncertainValue(lower, upper, Uniform)`コンストラクタを使用して形成されます。

```julia
# `[2, 3]`の一様分布
UncertainValue(-2, 3, Uniform)
```
