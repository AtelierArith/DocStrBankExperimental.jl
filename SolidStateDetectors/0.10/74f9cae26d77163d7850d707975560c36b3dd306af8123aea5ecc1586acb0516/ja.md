```
struct SolidStateDetector{T,SC,CT,PT,VDM} <: AbstractConfig{T}
```

固体検出器のすべての部分を説明する構造体、すなわち [`Semiconductor`](@ref)、一連の [`Contact`](@ref)、および（オプションで）[`Passive`](@ref) と仮想ドリフトボリューム。

部品の特性（電荷密度、固定電位、材料の相対誘電率）は、[`ElectricPotential`](@ref) および [`WeightingPotential`](@ref) の計算に入力として使用されます [`Simulation`](@ref) において。

## パラメトリック型

  * `T`: 精度タイプ。
  * `SC`: `semiconductor` の型。
  * `CT`: `contacts` の型。
  * `PT`: `passives` の型。
  * `VDM`: `virtual_drift_volumes` の型。

## フィールド

  * `name::String`: 検出器の名前。
  * `semiconductor::SC`: 検出器の [`Semiconductor`](@ref)。
  * `contacts::CT`: 検出器の [`Contact`](@ref) のベクター。
  * `passives::PT`: 検出器の周囲の構造を保持する [`Passive`](@ref) オブジェクトのベクター。
  * `virtual_drift_volumes::VDM`: ドリフトがユーザー定義の `modulate_driftvector` メソッドによって調整できる仮想ドリフトボリュームのベクター、例: [`DeadVolume`](@ref)。

さらに [`Semiconductor`](@ref)、[`Contact`](@ref)、[`Passive`](@ref) および [`DeadVolume`](@ref) を参照してください。
