```julia
mutable struct MCCallback{FH, FJ, C<:McCormick.AbstractContractorMC, PRE<:McCormick.AbstractPreconditionerMC, N, T<:McCormick.RelaxTag, AMAT<:(AbstractMatrix)} <: McCormick.AbstractMCCallback
```

暗黙の緩和を計算するために使用される構造体。

  * `h!::Any`: h(x,p) = 0 を h!(out,x,p) によってその場で定義する関数
  * `hj!::Any`: x に関する h(x,p) のヤコビアン
  * `H::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`: h! の出力のための中間的なその場ストレージ
  * `J::AbstractMatrix`: hj! の出力のための中間的なその場ストレージ
  * `J0::Vector{AMAT} where AMAT<:(AbstractMatrix)`
  * `xz0::Vector{AMAT} where AMAT<:(AbstractMatrix)`
  * `xmid::Vector{Float64}`
  * `X::Vector{IntervalArithmetic.Interval{Float64}}`: 状態空間 `x` の区間境界
  * `P::Vector{IntervalArithmetic.Interval{Float64}}`: 決定空間 `p` の区間境界
  * `nx::Int64`: 状態空間の次元
  * `np::Int64`: 決定空間の次元
  * `λ::Float64`: 凸結合パラメータ
  * `eps::Float64`: 区間の等価性に対する許容誤差
  * `kmax::Int64`: 取るべきコントラクタステップの数
  * `pref_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`: アフィン緩和が計算される参照決定点（およびその後の計算で使用される）。
  * `p_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`: 緩和が評価される決定点。
  * `p_temp_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`: gen*expansion*params! ルーチンで p を一時的に保存するために使用されるベクター。
  * `x0_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `x_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `xa_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `xA_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `aff_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `z_mc::Array{McCormick.MC{N, T}, 1} where {N, T<:McCormick.RelaxTag}`
  * `contractor::McCormick.AbstractContractorMC`: 暗黙の緩和ルーチンで使用されるコントラクタのタイプ。
  * `preconditioner::McCormick.AbstractPreconditionerMC`: 暗黙の緩和ルーチンで使用される前処理器。
  * `apply_precond::Bool`: 前処理器を適用すべきことを示すブール値
  * `param::Array{Array{McCormick.MC{N, T}, 1}, 1} where {N, T<:McCormick.RelaxTag}`: 中間計算で使用されるアフィン緩和を生成するために各反復での `x` の緩和のベクター。
  * `use_apriori::Bool`: 乗算のサブグラディエントベースの事前緩和を使用すべきことを示す。
