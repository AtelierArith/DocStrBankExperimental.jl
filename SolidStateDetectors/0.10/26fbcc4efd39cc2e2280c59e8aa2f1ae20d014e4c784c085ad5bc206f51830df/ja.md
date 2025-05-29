```
plot_electron_and_hole_contribution(evt::Event{T}, sim::Simulation{T}, contact_id::Int)
```

波形と、与えられた `contact_id` の [`Event`](@ref) に対する波形への電子およびホールの寄与をプロットします。

## 引数

  * `evt::Event{T}`: すでに電荷がドリフトされた [`Event`](@ref)。
  * `sim::Simulation{T}`: `evt` の電荷がドリフトされた設定を定義する [`Simulation`](@ref)。
  * `contact_id::Int`: 波形を電子およびホールの寄与に分割するための [`Contact`](@ref) の `id`。

## キーワード

  * `n_samples::Int`: 波形をプロットするためのサンプル数。デフォルトは元の波形のサンプル数です。

## 例

```julia
using Plots
using SolidStateDetector
T = Float32

simulation = Simulation{T}(SSD_examples[:InvertedCoax])
simulate!(simulation)
event = Event([CartesianPoint{T}(0.02,0.01,0.05)])
simulate!(event, simulation)

contact_id = 1
plot_electron_and_hole_contribution(evt, sim, contact_id, n_samples = 300)
```

!!! note
    `evt` のドリフトパスは、この関数を呼び出す前に [`drift_charges!`](@ref) を使用して計算する必要があります。


!!! note
    このメソッドは、パッケージ [Plots.jl](https://github.com/JuliaPlots/Plots.jl) をロードする必要があります。


他にも [`get_electron_and_hole_contribution`](@ref) を参照してください。 ```
