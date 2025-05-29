```
simulate!(evt::Event{T}, sim::Simulation{T}; kwargs...)::Nothing where {T <: SSDFloat}
```

指定された[`Simulation`](@ref)に対して[`Event`](@ref)の波形をシミュレートします。

1. `evt.locations`でのすべてのエネルギーヒットのドリフトパスを計算し、
2. `sim.weighting_potentials`で指定された[`WeightingPotential`](@ref)に対して各[`Contact`](@ref)の波形を生成します。

出力は`evt.drift_paths`と`evt.waveforms`に格納されます。

## 引数

  * `evt::Event{T}`: 電荷がドリフトすべき[`Event`](@ref)。
  * `sim::Simulation{T}`: `evt`内の電荷がドリフトすべきセットアップを定義する[`Simulation`](@ref)。

## キーワード

  * `max_nsteps::Int = 1000`: 各ヒットのドリフトにおける最大ステップ数。
  * `Δt::RealQuantity = 5u"ns"`: ドリフトに使用される時間ステップ。
  * `diffusion::Bool = false`: ランダムウォークによる電荷キャリアの拡散を有効または無効にします。
  * `self_repulsion::Bool = false`: 同じタイプの電荷キャリアの自己反発を有効または無効にします。
  * `verbose = true`: 追加情報の出力を有効または無効にします。

## 例

```julia
simulate!(evt, sim, Δt = 1u"ns", verbose = false)
```

[`drift_charges!`](@ref)および[`get_signals!`](@ref)も参照してください。
