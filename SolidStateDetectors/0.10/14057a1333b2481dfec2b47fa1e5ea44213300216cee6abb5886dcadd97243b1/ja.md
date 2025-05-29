```
get_electron_and_hole_contribution(evt::Event{T}, sim::Simulation{T}, contact_id::Int)
```

指定された `contact_id` の [`Event`](@ref) に対する波形の電子およびホールの寄与を、`electron_contribution` と `hole_contribution` の2つのエントリを持つ `NamedTuple` として返します。

## 引数

  * `evt::Event{T}`: すでに電荷がドリフトされた [`Event`](@ref)。
  * `sim::Simulation{T}`: `evt` の電荷がドリフトされた設定を定義する [`Simulation`](@ref)。
  * `contact_id::Int`: 波形を電子およびホールの寄与に分割するための [`Contact`](@ref) の `id`。

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
wf = get_electron_and_hole_contribution(evt, sim, contact_id)
```

!!! note
    この関数を呼び出す前に、`evt` のドリフトパスを [`drift_charges!`](@ref) を使用して計算する必要があります。


他にも [`plot_electron_and_hole_contribution`](@ref) を参照してください。 ```
