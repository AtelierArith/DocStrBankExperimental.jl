```
(timeSignal, signal, signalType) = ModiaResult.rawSignal(result, name)
```

結果データ構造 `result` と変数 `name::AbstractString` を考慮して、独立変数の結果値（= `timeSignal`）、対応する変数の結果値（= `signal`）、および信号のタイプ `signalType::`[`SignalType`](@ref) を返します。なお、`name` が不明な場合はエラーが発生します。

以下の図は、返される `timeSignal` と `signal` のデータ構造を示しています：

![SignalDefinition](https://modiasim.github.io/ModiaResult.jl/resources/images/signal-definition.png)

他の信号タイプは、ビューを導入することによってこの基本信号タイプにマッピングされる可能性があります。

# 返される引数の詳細

`timeSignal::Vector{Vector{T1}}`: 結果は1つ以上の**セグメント**で構成されます。`timeSignal[i][j]` はセグメント `i` における時間瞬間 `j` の値です。`timeSignal[i][:]` は単調増加の値を持ち、型 `T1<:Real` は `Real` のサブタイプであり、`AbstractFloat` への変換が定義されている必要があります。例えば、`T1::Rational` は問題ありませんが、`T1::Complex` は許可されていません。

`signal::Vector{Vector{T2}}` または `signal::Vector{Vector{Array{T2,N}}}`: `signal[i][j]` は時間瞬間 `timeSignal[i][j]` における変数の値です。この値はスカラーまたは配列である可能性があります。型 `T2` は以下のいずれかの値を持つことができます：

  * `T2 <: Real`、`AbstractFloat` への変換が定義されている `Real` のサブタイプ、または
  * `T2 <: Measurements.Measurement{T1}`、または
  * `T2 <: MonteCarloMeasurements.StaticParticles{T1,N}`、または
  * `T2 <: MonteCarloMeasurements.Particles{T1,N}`。

信号が値 `value` の定数である場合、`([[t_min, t_max]], [[value, value]], ModiaResult.Continuous)` を返します。

信号が時間信号である場合、`(timeSignal, timeSignal, ModiaResult.independent)` を返します。`timeSignal` は、結果の最初と最後の時間点からなるダミーベクターである可能性があります（異なる信号に対して異なる `timeSignals` が存在する場合や、信号が定数である場合）。

`signal` と `timeSignal` は、パッケージ `Unitful` からの単位を持つ場合があります。

情報 `signalType::SignalType` は、信号がどのように補間および/またはプロットできるかを定義します。
