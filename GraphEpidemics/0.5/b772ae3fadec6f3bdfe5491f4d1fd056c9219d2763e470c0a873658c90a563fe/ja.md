`run_sir_gillespie(g::AbstractGraph, model::AbstractSIRModel, rng::AbstractRNG, patient_zeros::Vector{<:Integer}; dtype=Float64, kwargs...)`

シミュレーションデータを設定し、モデルに従って回復遅延を引いたGillespie SIRシミュレーションを実行します。

### オプション引数

  * `dtype`: シミュレーション配列のデータ型。デフォルトは `Float64`。
