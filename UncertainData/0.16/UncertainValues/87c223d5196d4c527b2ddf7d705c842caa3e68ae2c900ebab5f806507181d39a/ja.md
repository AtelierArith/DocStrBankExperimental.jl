```
UncertainValue(distribution::Type{D}, a::T1, b::T2, c::T3;
    kwargs...) where {T1<:Number, T2<:Number, T3<:Number, D<:Distribution}
```

## 三パラメータ分布のコンストラクタ

現在実装されている分布は `BetaBinomial` です。

### 引数

  * **`a`, `b`, `c`**: 提供される `distribution` によって意味が異なる一般的なパラメータ。以下のリストを参照してください。
  * **`distribution`**: `Distributions.jl` からの有効な単変量分布。

`a`, `b` および `c` が何であるかは、提供される分布によって異なります。

  * `UncertainValue(BetaBinomial, n, α, β)` は `UncertainScalarBetaBinomialDistributed` インスタンスを返します。

### キーワード引数

  * **`nσ`**: `distribution <: Distributions.Normal` の場合、`lower` と `upper`（すなわち両方、なぜならそれらは `μ` から同じ距離にあるため）が `μ` からどれだけの標準偏差の距離にあるか？
  * **`tolerance`**: 正規分布の構築を許可するために不確実性がどれだけ対称でなければならないかを決定する閾値（`upper - lower > threshold` が必要です）。
  * **`trunc_lower`**: 無限サポートを持つ分布の下限切断境界。デフォルトは `-Inf`。
  * **`trunc_upper`**: 無限サポートを持つ分布の上限切断境界。デフォルトは `Inf`。

## 例

### BetaBinomial 分布

正規分布は、コンストラクタ `UncertainValue(μ, σ, Normal; kwargs...)` を使用して形成されます。これにより、平均 μ および標準偏差 σ/nσ の正規分布が得られます（nσ はキーワード引数として指定する必要があります）。

```julia
# n = 100 試行とパラメータ α = 2.3 および
# β = 5 のベータ二項分布
UncertainValue(100, 2.3, 5, BetaBinomial)
```
