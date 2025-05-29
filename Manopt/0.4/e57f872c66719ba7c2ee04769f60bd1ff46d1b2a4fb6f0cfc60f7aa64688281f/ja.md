```
InteriorPointNewtonState <: AbstractHessianSolverState
```

# フィールド

  * `λ`:           等式制約に関するラグランジュ乗数
  * `μ`:           不等式制約に関するラグランジュ乗数
  * `p`:           現在の反復点
  * `s`:           現在のスラック変数
  * `sub_problem`: サブソルバーのための [`AbstractManoptProblem`](@ref) 問題
  * `sub_state`:   サブソルバーのための [`AbstractManoptSolverState`](@ref)
  * `X`:           `p` に関する現在の勾配
  * `Y`:           `μ` に関する現在の勾配
  * `Z`:           `λ` に関する現在の勾配
  * `W`:           `s` に関する現在の勾配
  * `ρ`:           サブ問題でバリアパラメータ `β` を計算するために `μ's/m` の直交性を保存
  * `σ`:           サブ問題でのバリアパラメータ `β` のスケーリングファクター
  * `stop`: [`StoppingCriterion`](@ref) で、いつ停止するかを示す
  * `retraction_method`: `M` に対して使用する再収束法
  * `stepsize::`[`Stepsize`](@ref): 使用するステップサイズ
  * `step_problem`: ラインサーチのための多様体と目的を格納する [`AbstractManoptProblem`](@ref)
  * `step_state`: ラインサーチの状態で反復点と探索方向を格納、[`StepsizeState`](@ref) を参照

# コンストラクタ

```
InteriorPointNewtonState(
    M::AbstractManifold,
    cmo::ConstrainedManifoldObjective,
    p,
    sub_problem::Pr,
    sub_state::St;
    kwargs...
)
```

状態を初期化します。ここで、[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`) と [`ConstrainedManifoldObjective`](@ref) の両方がキーワードの合理的なデフォルトを埋めるために使用されます。

# 入力

  * `M`:           リーマン多様体
  * `cmo`:         [`ConstrainedManifoldObjective`](@ref)
  * `p`:           アルゴリズムの初期点としての `M` 上の点
  * `sub_problem`: サブソルバーのための [`AbstractManoptProblem`](@ref) 問題
  * `sub_state`:   サブソルバーのための [`AbstractManoptSolverState`](@ref)

# キーワード引数

不等式制約の数を `m`、等式制約の数を `n` とします。

  * `μ=ones(m)`
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M,p)`
  * `Y=zero(μ)`
  * `λ=zeros(n)`
  * `Z=zero(λ)`
  * `s=ones(m)`
  * `W=zero(s)`
  * `ρ=μ's/m`
  * `σ=`[`calculate_σ`](@ref)`(M, cmo, p, μ, λ, s)`
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenChangeLess`](@ref)`(1e-8)`
  * `retraction_method=default_retraction_method(M, typeof(p))`
  * `step_objective=`[`ManifoldGradientObjective`](@ref)`(`[`KKTVectorFieldNormSq`](@ref)`(cmo)`, [`KKTVectorFieldNormSqGradient`](@ref)`(cmo)`; evaluation=[`InplaceEvaluation`](@ref)`())`
  * `vector_space=`[`Rn`](@ref Manopt.Rn): 整数を与えると、ベクトル空間成分 $ℝ^m,ℝ^n$ に使用される多様体を返す関数
  * `step_problem`: 多様体 $\mathcal M × ℝ^m × ℝ^n × ℝ^m$ をラップ
  * `step_state`: 点と探索方向を持つ [`StepsizeState`](@ref)
  * `stepsize`: [`ArmijoLinesearch`](@ref) で、ステップを受け入れるための追加条件として [`InteriorPointCentralityCondition`](@ref) を持つ。注意：このステップサイズは独自の `step_problem` と `step_state` で動作します。

内部的に `_step_M` と `_step_p` はステップサイズのための多様体と点です。
