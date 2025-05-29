```
calculate_capacitance_matrix(sim::Simulation{T}; consider_multiplicity::Bool = true) where {T}
```

マクスウェルキャパシタンス `N×N`-行列をpF単位で計算します。ここで、`N`は`sim.detector`の接点の数です。個々の要素、$c_{i,j}$は、[`calculate_mutual_capacitance(sim::Simulation, (i,j)::Tuple{Int,Int})`](@ref)を介して計算されます。行列は対称であるべきです。`C[i,j]`と`C[j,i]`の違いは、2つの重み付けポテンシャルの異なるグリッドによる数値精度のためです。

## 引数

  * `sim::Simulation`: キャパシタンス行列が計算される[`Simulation`](@ref)。

## キーワード

  * `consider_multiplicity::Bool = true`: システムの対称性を考慮するかどうか。例えば、真の同軸検出器が原点を中心にし、`x-axis`が`[0, x_max]`、`y-axis`が`[0, y_max]`の直交グリッド上で計算される場合、重複度は4であり、`consider_multiplicity == true`の場合、返される値はすでに4倍されています。
