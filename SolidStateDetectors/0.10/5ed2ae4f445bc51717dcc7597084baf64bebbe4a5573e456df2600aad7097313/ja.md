```
calculate_mutual_capacitance(sim::Simulation, ij::Tuple{Int, Int}; consider_multiplicity::Bool = true)
```

ID `i = ij[1]` と `j = ij[2]` の接点間の相互キャパシタンスを返します。これは、接点の重み付けポテンシャル $\Phi_i^w(\vec{r})$ と $\Phi_j^w(\vec{r})$ を用いて計算されます：

$$
c_{ij} = \epsilon_0 \int_{World} \nabla \Phi_i^w(\vec{r}) ϵ_r(\vec{r}) \nabla \Phi_j^w(\vec{r}) d\vec{r}
$$

!!! note
    これらはマクスウェルキャパシタンス行列の要素です。詳細については [Capacitances](@ref) を参照してください。


!!! note
    電気ポテンシャルと両接点の2つの重み付けポテンシャルを計算する必要があります。


## 引数

  * `sim::Simulation`: キャパシタンス行列が計算される [`Simulation`](@ref)。
  * `ij::Tuple{Int,Int}`: キャパシタンスを計算する接点のインデックスのタプル。

## キーワード

  * `consider_multiplicity::Bool = true`: システムの対称性を考慮するかどうか。例えば、真の同軸検出器が原点を中心にしており、`x-axis` が `[0, x_max]` から、`y-axis` が `[0, y_max]` までの直交座標グリッドで計算される場合、重複度は4であり、`consider_multiplicity == true` の場合、返される値はすでに4倍されています。
