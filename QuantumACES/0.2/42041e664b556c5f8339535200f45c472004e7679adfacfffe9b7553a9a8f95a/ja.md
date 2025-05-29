```
設計
```

回路のノイズ特性評価実験のための実験設計。

# フィールド

  * `c::AbstractCircuit`: 設計によって特性評価された回路。
  * `full_covariance::Bool`: `true` の場合、`covariance_dict_ensemble` にフル共分散行列を構築するためのパラメータを生成し、`false` の場合は対角線上の項を構築するためのパラメータのみを生成します。
  * `matrix::SparseMatrixCSC{Int32, Int32}`: M 回路固有値と N ゲート固有値に対応するスパース M x N 設計行列。
  * `tuple_set::Vector{Vector{Int}}`: 回路層を配置するタプルのセット。
  * `tuple_set_data::TupleSetData`: タプルセットを生成する [`TupleSetData`](@ref) オブジェクト。
  * `mapping_ensemble::Vector{Vector{Mapping}}`: 各タプルに対してそのタプルに対応するパウリの回路固有値のための [`Mapping`](@ref) オブジェクトのベクター。
  * `experiment_ensemble::Vector{Vector{Vector{Int}}}`: 各タプルに対して同時に準備可能で測定可能な回路固有値に対応する [`Mapping`](@ref) オブジェクトをインデックスする実験のベクター。
  * `covariance_dict_ensemble::Vector{Dict{CartesianIndex{2}, Tuple{Mapping, Int}}}`: 各タプルに対して、スパース回路固有値推定器共分散行列の非ゼロエントリを記述する [`Mapping`](@ref) オブジェクトの辞書と、実験セットによってそのエントリが推定される回数。
  * `prep_ensemble::Vector{Vector{Layer}}`: 各タプルに対して、セット内の各実験のためにパウリ固有状態でキュービットを準備する [`Layer`](@ref) オブジェクトのベクター。
  * `meas_ensemble::Vector{Vector{Layer}}`: 各タプルに対して、セット内の各実験のためにパウリ基底でキュービットを測定する [`Layer`](@ref) オブジェクトのベクター。
  * `tuple_times::Vector{Float64}`: セット内の各タプルによって配置された回路を実装するのにかかる時間で、基本タプルセットの時間係数に応じて正規化されています。
  * `shot_weights::Vector{Float64}`: セット内の各タプルのショットウェイトで、合計は 1 になります。
  * `experiment_numbers::Vector{Int}`: セット内の各タプルの実験数。
  * `experiment_number::Int`: 実験の総数。
  * `calculation_times::Matrix{Float64}`: 各タプルの設計のコンポーネントを生成するのにかかる時間で、マッピング、タプル一貫性のあるパウリ準備のセット、実験セット、および共分散行列辞書の生成に対応します。
  * `overall_time::Float64`: 設計を生成するのにかかる全体の時間。
  * `optimisation_time::Float64`: 設計を最適化するのにかかる時間。
  * `ls_type::Symbol`: ショットウェイトが最適化された最小二乗のタイプ。
