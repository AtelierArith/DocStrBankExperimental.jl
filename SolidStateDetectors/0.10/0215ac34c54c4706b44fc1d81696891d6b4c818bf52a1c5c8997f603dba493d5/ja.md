```
calculate_electric_field!(sim::Simulation{T}; n_points_in_φ::Union{Missing, Int} = missing)::Nothing
```

[`ElectricField`](@ref)を`sim.electric_potential`に格納された[`ElectricPotential`](@ref)から計算し、`sim.electric_field`に保存します。

## 引数

  * `sim::Simulation{T}`: `sim.electric_potential`がすでに計算されている[`Simulation`](@ref)。

## キーワード

  * `n_points_in_φ::Union{Missing, Int}`: 2Dの[`ElectricPotential`](@ref)（円筒座標で`φ`に対して対称）に対して、`sim.electric_potential`は3Dの[`ElectricField`]を計算するために`φ`において`n_points_in_φ`の「層」に拡張されます。`n_points_in_φ`が`missing`の場合、デフォルト値は`36`です。

## 例

```
calculate_electric_field!(sim, n_points_in_φ = 32)
```

!!! note
    このメソッドは、`sim.electric_potential`がすでに計算されており、`missing`でない場合にのみ機能します。

