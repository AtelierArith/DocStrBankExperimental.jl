```
calculate_stored_energy(sim::Simulation; consider_multiplicity::Bool = true)
```

指定された [`Simulation`](@ref) における [`SolidStateDetector`](@ref) の [`ElectricField`](@ref) に蓄えられたエネルギーを計算して返します。単位は J です。

## 引数

  * `sim::Simulation{T}`: 蓄えられたエネルギーが計算される `sim.detector` を持つ [`Simulation`](@ref)。

## キーワード

  * `consider_multiplicity::Bool = true`: システムの対称性を考慮するかどうか。例えば、真の同軸検出器が原点を中心にしており、`x-axis` が `[0, x_max]` から、`y-axis` が `[0, y_max]` までの直交座標グリッドで計算される場合、重複度は 4 であり、`consider_multiplicity == true` の場合、返される値はすでに 4 で乗算されています。
