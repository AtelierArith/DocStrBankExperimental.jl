```
lmsolve(
    fun,
    jac,
    x0::StaticVector{N, <:AbstractFloat},
    data = nothing,
    lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing,
    ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing;
    kwargs...
) -> x, F, info, iter, nfev, njev

lmsolve!(
    fun!,
    jac!,
    x0::AbstractVector{<:AbstractFloat},
    m::Integer = length(x0),
    data = nothing,
    lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing,
    ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing;
    kwargs...,
) -> x, F, info, iter, nfev, njev, LM, solver

lmsolve!(
    fun!,
    jac!,
    x0::AbstractVector{<:AbstractFloat},
    f::AbstractVector{<:AbstractFloat},
    J::AbstractMatrix{<:AbstractFloat},
    data = nothing,
    lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing,
    ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing;
    kwargs...,
) -> x, F, info, iter, nfev, njev, LM, solver

lmsolve!(
    fun!,
    jac!,
    LM::LMWorkspace,
    data = nothing,
    lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing,
    ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing;
    kwargs...
) -> x, F, info, iter, nfev, njev, LM, solver
```

`F(x) = ||f(x)||^2` を最小化するために、レーベンバーグ・マルカートアルゴリズムを使用します。

### 引数

  * `fun/fun!`: 最小化される関数 `||f||^2`、`f = fun(x, data)`、`f = fun!(f, x, data)`
  * `jac/jac!`: `f` のヤコビアン、`J = jac(x, data)`、`J = jac!(J, x, data)`
  * `x0::AbstractVector{<:AbstractFloat}`: 初期推定値
  * `m::Integer = length(x0)`: 関数値の数
  * `data = nothing`: `fun/fun!` と `jac/jac!` に渡されるデータ
  * `f::AbstractVector{<:AbstractFloat}`: 事前に割り当てられた関数ベクトル
  * `J::AbstractMatrix{<:AbstractFloat}`: 事前に割り当てられたヤコビアン行列
  * `LM::LMWorkspace`: 事前に割り当てられたワークスペース
  * `lb::Union{Nothing, Real, AbstractVector{<:Real}} = nothing`: `x` の下限。ベクトルは `x` と同じ長さでなければなりません
  * `ub::Union{Nothing, Real, AbstractVector{<:Real}} = nothing`: `x` の上限。ベクトルは `x` と同じ長さでなければなりません

### キーワード

  * `solver::Union{Nothing, Symbol} = nothing`: `lmsolve!` の線形ソルバー (`lmsolve` は常にコレスキー分解を使用します)

      * `nothing`: 密なヤコビアンの場合はQR、疎なヤコビアンの場合はコレスキー
      * `:cholesky`: コレスキー分解
      * `:qr`: QR分解
  * `ftol::Real = eps(eltype(x))`: 関数の相対許容誤差: 実際の減少と予測された減少の両方が `ftol` より小さい
  * `xtol::Real = 1e-10`: `x` の変化に対する相対許容誤差: `all(abs(x - xk) < xtol * (xtol + abs(x)))`
  * `gtol::Real = eps(eltype(x))`: 勾配の許容誤差: `norm(g, Inf) < gtol`
  * `maxit::Integer = 1000`: 最大反復回数
  * `factor::Real = 1e-6`: ダンピングの初期係数
  * `factoraccept::Real = 13`: 良いステップでのダンピングを減少させるための係数
  * `factorreject::Real = 3`: 悪いステップでのダンピングを増加させるための係数
  * `factorupdate::Symbol = :marquardt`: 係数更新方法 `∈ (:marquardt, :nielsen)`
  * `minscale::Real = 1e-12`: 対角スケーリングの下限
  * `maxscale::Real = 1e16`: 対角スケーリングの上限
  * `minfactor::Real = 1e-28`: ダンピング係数の下限
  * `maxfactor::Real = 1e32`: ダンピング係数の上限

### 戻り値

  * `x/LM.x`: 解
  * `F`: 最終目的
  * `info::Int`: 収束状態

      * `1`: 実際の減少と予測された減少の両方が `ftol` より小さい
      * `2`: 2つの連続した反復の相対差が `xtol` より小さい
      * `3`: 勾配の無限ノルムが `gtol` より小さい
      * `-1`: `maxit` に達した
  * `iter::Int`: 反復回数
  * `nfev::Int`: 関数評価の回数
  * `njev::Int`: ヤコビアン評価の回数
  * `LM::LMWorkspace`: ワークスペース
  * `solver::AbstractSolver`: ソルバー

### 注意事項

返された `LMWorkspace` では、`LM.x` と `LM.f` のみが更新されることが保証されています。つまり、`LM.J` は返された `x` でのヤコビアンではない可能性があります。
