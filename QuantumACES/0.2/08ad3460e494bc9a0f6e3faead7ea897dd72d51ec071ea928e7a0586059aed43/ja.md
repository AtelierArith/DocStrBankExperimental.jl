```
RandDesign
```

実験デザインのためのパウリフレームランダム化実験アンサンブル。

# フィールド

  * `d::Design`: 実験デザイン。
  * `pauli_randomisation_ensemble::Vector{Vector{Vector{Vector{String}}}}`: 各タプル、実験、およびランダム化に対して、ランダム化回路内の各層間のパウリフレームランダム化のベクトル。
  * `pauli_sign_ensemble::Vector{Vector{Vector{Vector{Bool}}}}`: 各タプル、実験、およびランダム化に対して、ランダム化実験によって推定されたパウリの符号のベクトル。
  * `covariance_pauli_sign_ensemble::Vector{Vector{Vector{Vector{Bool}}}}`: 各タプル、実験、およびランダム化に対して、ランダム化実験によって推定された共分散パウリの符号のベクトル。
  * `job_indices::Vector{Vector{NTuple{3, Int}}}`: 各ジョブに対して、ジョブ内の各回路のインデックス（タプル、実験、ランダム化）のベクトル。
  * `randomisations::Vector{Int}`: デザイン内の各タプルに対応する実験セットのランダム化の数。
  * `shot_budget::Int`: ランダム化実験アンサンブルのショット予算。
  * `experiment_shots::Int`: ランダム化実験アンサンブル内の各実験のショット数。
  * `seed::UInt64`: ランダム化実験アンサンブルを生成するために使用されるランダムシード。
