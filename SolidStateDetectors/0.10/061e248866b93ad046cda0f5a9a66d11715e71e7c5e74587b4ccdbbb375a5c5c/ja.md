```
drift_charges!(evt::Event{T}, sim::Simulation{T}; kwargs...)::Nothing where {T <: SSDFloat}
```

与えられた [`Event`](@ref) と [`Simulation`](@ref) のために電子とホールのドリフトパスを計算し、それらを `evt.drift_paths` に格納します。

## 引数

  * `evt::Event{T}`: チャージをドリフトさせるための [`Event`](@ref)。
  * `sim::Simulation{T}`: `evt` のチャージがドリフトする設定を定義する [`Simulation`](@ref)。

## キーワード

  * `max_nsteps::Int = 1000`: 各ヒットのドリフトにおける最大ステップ数。
  * `Δt::RealQuantity = 5u"ns"`: ドリフトに使用される時間ステップ。
  * `diffusion::Bool = false`: ランダムウォークによるチャージキャリアの拡散を有効または無効にします。
  * `self_repulsion::Bool = false`: 同じタイプのチャージキャリアの自己反発を有効または無効にします。
  * `verbose = true`: 追加情報の出力を有効または無効にします。

## 例

```julia
drift_charges!(evt, sim, Δt = 1u"ns", verbose = false)
```

!!! note
    `Δt` に単位を持つ値を使用するには、パッケージ [Unitful.jl](https://github.com/PainterQubits/Unitful.jl) が必要です。

