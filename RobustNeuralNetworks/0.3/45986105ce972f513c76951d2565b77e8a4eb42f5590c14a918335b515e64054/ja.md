```
SandwichFC((in, out), σ::F; <keyword arguments>) where F
```

密な（完全接続）LBDNのための非拡張「サンドイッチ層」を構築します。

非拡張層とは、リプシッツ境界が正確に1である層です。この層は、[`Flux.Dense`](https://fluxml.ai/Flux.jl/stable/models/layers/#Flux.Dense)のリプシッツ境界付きの代替として提供されます。そのインターフェースと使用法は、Fluxに慣れている人が簡単に使用できるように非常に似た形で意図的に設計されています。

# 引数

  * `(in, out)::Pair{<:Integer, <:Integer}`: 層の入力サイズと出力サイズ。
  * `σ::F=identity`: 活性化関数。

# キーワード引数

  * `init::Function=Flux.glorot_normal`: すべての重みとバイアスベクトルの初期化関数。
  * `bias::Bool=true`: バイアスベクトルを含めるかどうか。
  * `output_layer::Bool=false`: 密なLBDNの出力層または通常のサンドイッチ層。
  * `T::DataType=Float32`: 重み行列とバイアスベクトルのデータ型。
  * `rng::AbstractRNG = Random.GLOBAL_RNG`: モデル初期化のためのrng。

# 例

`SandwichFC`層を使用して直接密なLBDNを構築できます。モデル構造は、[Wang & Manchester (2023)](https://proceedings.mlr.press/v202/wang23v.html)の式8に記載されています。

```jldoctest
using Flux
using Random
using RobustNeuralNetworks

# 一貫性のためのランダムシード
rng = Xoshiro(42)

# モデル仕様
nu = 1                  # 入力の数
ny = 1                  # 出力の数
nh = fill(16,2)         # 2つの隠れ層、それぞれ16ニューロン
γ = 5                   # リプシッツ境界5.0

# 密なLBDNモデルのセットアップ
model = Flux.Chain(
    (x) -> (√γ * x),
    SandwichFC(nu => nh[1], relu; T=Float64, rng),
    SandwichFC(nh[1] => nh[2], relu; T=Float64, rng),
    (x) -> (√γ * x),
    SandwichFC(nh[2] => ny; output_layer=true, T=Float64, rng),
)

# ダミー入力で評価
u = 10*randn(rng, nu, 10)
y = model(u)

println(round.(y;digits=2))

# 出力

[4.13 4.37 3.22 8.38 4.15 3.71 0.7 2.04 1.78 2.64]
```

[`DenseLBDNParams`](@ref)や[`DiffLBDN`](@ref)も参照してください。
