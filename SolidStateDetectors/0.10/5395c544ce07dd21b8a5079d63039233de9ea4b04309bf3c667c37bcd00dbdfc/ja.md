```
estimate_depletion_voltage(sim::Simulation{T},
    Umin::T = minimum(broadcast(c -> c.potential, sim.detector.contacts)),
    Umax::T = maximum(broadcast(c -> c.potential, sim.detector.contacts));
    contact_id::Int = determine_bias_voltage_contact_id(sim.detector),
    tolerance::AbstractFloat = 1e-1,
    verbose::Bool = true) where {T <: AbstractFloat}
```

指定された [`Simulation`](@ref) において、`contact_id` での [`Contact`](@ref) を完全に枯渇させるために必要な電位を二分法で推定します。デフォルトの `contact_id` は `determine_bias_voltage_contact_id(sim.detector)` によって自動的に決定されます。電位のデフォルト検索範囲は接触電位の極値によって設定されます。

## 引数

  * `sim::Simulation{T}`: 枯渇電圧を決定するための [`Simulation`](@ref)。
  * `Umin::T`: 検索範囲の最小値。
  * `Umax::T`: 検索範囲の最大値。

## キーワード

  * `contact_id::Int`: 電位が適用される [`Contact`](@ref) の `id`。
  * `tolerance::AbstractFloat`: 結果の許容精度。デフォルトは 1e-1。
  * `verbose::Bool = true`: 追加情報の出力を有効または無効にします。デフォルトは `true`。

## 例

```julia
using SolidStateDetectors
sim = Simulation(SSD_examples[:InvertedCoax])
calculate_electric_potential!(sim)
estimate_depletion_voltage(sim)
```

!!! note
    結果の精度は初期シミュレーションの精度に依存します。


!!! note
    この関数は、`sim` に応じて2Dまたは3Dのフィールド計算を2回実行します。 したがって、いくつかのメモリを消費する可能性があることに注意してください。


関連情報として [`is_depleted`](@ref) も参照してください。
