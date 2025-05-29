```
abstract type AbstractLBDN{T, L} end
```

リプシッツ有界深層ネットワークの明示的パラメータ化。

```
(m::AbstractLBDN)(u::AbstractVecOrMat)
```

入力 `u` を与えた `AbstractLBDN` モデルの呼び出し。

引数が行列の場合、各列は入力のベクトルでなければならず（バッチシミュレーションを許可）。

# 例

この例では、[`DenseLBDNParams`](@ref) を使用して密な [`LBDN`](@ref) を作成し、いくつかのランダムに生成された入力でモデルを呼び出します。

```jldoctest
using Random
using RobustNeuralNetworks

# セットアップ
rng = Xoshiro(42)
batches = 10
γ = 20.0

# 4つの入力、1つの出力、4つの隠れ層を持つモデル
nu, ny = 4, 1
nh = [5, 10, 5, 15]

lbdn_ps = DenseLBDNParams{Float64}(nu, nh, ny, γ; rng)
lbdn = LBDN(lbdn_ps)

# ランダムな入力のバッチでモデルを評価
u = 10*randn(rng, nu, batches)
y = lbdn(u)

println(round.(y; digits=2))

# 出力

[-1.11 -1.01 -0.07 -2.25 -4.22 -1.76 -3.82 -1.13 -11.85 -3.01]
```
