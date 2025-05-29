```
simulate_waveforms( mcevents::TypedTables.Table, sim::Simulation{T}; kwargs...)
simulate_waveforms( mcevents::TypedTables.Table, sim::Simulation{T}, output_dir::AbstractString, output_base_name::AbstractString; kwargs...)
```

`mcevents`で定義されたすべてのイベントの波形を、指定された[`Simulation`](@ref)に対してシミュレートします。

1. `mcevents`で定義されたすべてのエネルギーヒットのドリフトパスを計算します。
2. `sim.weighting_potentials`で指定された[`WeightingPotential`](@ref)に対して、各[`Contact`](@ref)の信号（波形）を決定します。

## 引数

  * `mcevents::TypedTables.Table`: シミュレーションされたセットアップ内のイベントに関する情報を含むテーブル。
  * `sim::Simulation{T}`: `mcevents`内の電荷がドリフトすべきセットアップを定義する[`Simulation`](@ref)。

[LegendHDF5IO.jl](https://github.com/legend-exp/LegendHDF5IO.jl)がロードされている場合、この関数には追加の引数があります。

## 追加の引数（`LegendHDF5IO`）

  * `output_dir::AbstractString`: HDF5出力ファイルが保存されるディレクトリ。
  * `output_base_name::AbstractString`: HDF5出力ファイルのベース名、デフォルトは`"generated_waveforms"`です。

## キーワード

  * `max_nsteps::Int = 1000`: 各ヒットのドリフトにおける最大ステップ数。
  * `Δt::RealQuantity = 4u"ns"`: ドリフトに使用される時間ステップ。
  * `diffusion::Bool = false`: 電荷キャリアのランダムウォークによる拡散を有効または無効にします。
  * `self_repulsion::Bool = false`: 同じタイプの電荷キャリアの自己反発を有効または無効にします。
  * `number_of_carriers::Int = 1`: エネルギー沈着のN体シミュレーションで使用される電荷キャリアの数。
  * `number_of_shells::Int = 1`: エネルギー沈着の`center`点の周りのシェルの数。
  * `max_interaction_distance = NaN`: 電荷雲が相互作用する最大距離（`NaN`の場合、すべての電荷雲は独立してドリフトします）。
  * `verbose = false`: 追加情報の出力を有効または無効にします。
  * `chunk_n_physics_events::Int = 1000`（`LegendHDF5IO`のみ）: 単一のHDF5出力ファイルに保存されるべきイベントの数。

## 例

```julia
simulate_waveforms(mcevents, sim, Δt = 1u"ns", verbose = false)
# => 生成された波形が格納された追加の列`waveform`を持つ入力テーブル`mcevents`を返します
```

```julia
using LegendHDF5IO
simulate_waveforms(mcevents, sim, "output_dir", "my_basename", Δt = 1u"ns", verbose = false)
# => 電荷のドリフトをシミュレートし、出力を"output_dir/my_basename_evts_xx.h5"に保存します
```

!!! note
    ドリフトパスは一時的に計算されるだけで、返されません。


!!! note
    `Δt`に単位を持つ値を使用するには、パッケージ[Unitful.jl](https://github.com/PainterQubits/Unitful.jl)が必要です。

