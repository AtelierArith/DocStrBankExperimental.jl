```
LanczosState{P,T,SC,B,I,R,TM,V,Y} <: AbstractManoptSolverState
```

ランツォス反復を用いて適応的正則化サブプロブレムを解く

# フィールド

  * `stop::StoppingCriterion`: 停止基準が満たされたことを示すファンクタ
  * `stop_newton::StoppingCriterion`: 内部ニュートン反復のために使用される停止基準が満たされたことを示すファンクタ
  * `σ`:               現在の正則化パラメータ
  * `X`:               反復
  * `Lanczos_vectors`: 得られたランツォスベクトル
  * `tridig_matrix`:   三重対角係数行列 T
  * `coefficients`:    解を決定する係数 $y_1,...y_k$
  * `Hp`:              ヘッセ行列の評価を含む一時的な接ベクトル
  * `Hp_residual`:     ヘッセ行列に対する残差を含む一時的な接ベクトル
  * `S`:               現在得られた/近似された解

# コンストラクタ

```
LanczosState(TpM::TangentSpace; kwargs...)
```

## キーワード引数

  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M, p)`: 多様体 $\mathcal M$ の点 $p$ における接ベクトルとしての反復
  * `maxIterLanzcos=200`: `stopping_crtierion=` における最大反復回数を設定するショートカット
  * `θ=0.5`: デフォルトの `stopping_criterion=` 内の [`StopWhenFirstOrderProgress`](@ref) のパラメータを設定
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(maxIterLanczos)`[`|`](@ref StopWhenAny)[`StopWhenFirstOrderProgress`](@ref)`(θ)`: 停止基準が満たされたことを示すファンクタ
  * `stopping_criterion_newton=`[`StopAfterIteration`](@ref)`(200)`: 内部ニュートン反復のために使用される停止基準が満たされたことを示すファンクタ
  * `σ=10.0`: 正則化パラメータを指定
