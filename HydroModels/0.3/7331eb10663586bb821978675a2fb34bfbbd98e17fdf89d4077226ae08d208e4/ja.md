```
NeuralBucket{N} <: AbstractBucket
```

水文学モデルのための再帰的ニューラルネットワークベースのバケットで、Lux.jlの再帰層を活用しています。

# フィールド

  * `fluxes::Vector{<:AbstractHydroFlux}`: 適用されるプロセス関数のリスト。
  * `dfluxes::Vector{<:AbstractStateFlux}`: 状態更新のための状態導関数のリスト。
  * `func::Function`: 効率的な評価のための事前コンパイルされた再帰的ニューラルネットワーク関数。
  * `infos::NamedTuple`: 入力、出力、状態、パラメータ、ニューラルネットワーク名を含むメタデータ。

# コンストラクタ

```julia
NeuralBucket(; name=nothing, fluxes, dfluxes)
```

  * `name::Union{Symbol,Nothing}`: バケットのオプションの識別子。自動生成された名前がデフォルトです。
  * `fluxes::Vector{<:AbstractHydroFlux}`: 必須。主な計算要素。
  * `dfluxes::Vector{<:AbstractStateFlux}`: 必須。再帰的更新のための状態導関数。

# 使用例

```julia
bucket = NeuralBucket(
    name = :neural_bucket,
    fluxes = [HydroFlux(...), NeuralFlux(...)],
    dfluxes = [StateFlux(...)]
)
```

NeuralBucketは、Lux.jlの再帰層を使用して時間に沿った状態更新を処理することでHydroBucketと異なり、特にシーケンスモデリングタスクに適しています。
