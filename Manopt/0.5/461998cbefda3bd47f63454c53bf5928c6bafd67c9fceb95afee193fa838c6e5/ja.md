```
interior_point_Newton(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
interior_point_Newton(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
interior_point_Newton!(M, f, grad]_f, Hess_f, p; kwargs...)
interior_point_Newton(M, ConstrainedManifoldObjective, p; kwargs...)
```

次の制約付き問題を解決するために、内部点ニュートン法を実行します。

$$
\begin{aligned}
\operatorname*{arg\,min}_{p ∈ \mathcal M} & f(p)\\
\text{subject to}\quad&g_i(p) ≤ 0 \quad \text{ for } i= 1, …, m,\\
\quad & h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

このアルゴリズムは、スラック変数 `s` を用いて KKT 系を拡張することに基づいて線形システムを反復的に解決します。

$$
\operatorname{J} F(p, μ, λ, s)[X, Y, Z, W] = -F(p, μ, λ, s),
\text{ where }
X ∈ T_{p}\mathcal M, Y,W ∈ ℝ^m, Z ∈ ℝ^n,
$$

縮約形については、[`CondensedKKTVectorFieldJacobian`](@ref) と [`CondensedKKTVectorField`](@ref) をそれぞれ参照してください。通常、これが解決されます。縮約形の結果として得られた `X` と `Z` から、他の2つ、$Y$、$W$ が計算されます。

現在の反復点 $(p, μ, λ, s)$ における勾配 $(X,Y,Z,W)$ から、KKTベクトル場のノルム（平方）[`KKTVectorFieldNormSq`](@ref) とその勾配 [`KKTVectorFieldNormSqGradient`](@ref) を使用して線形探索が行われ、[`InteriorPointCentralityCondition`](@ref) と共に実行されます。

ベクトル場 $F$ には制約関数 $g, h$ の勾配が含まれているため、その勾配またはヤコビアンは制約のヘッセ行列を必要とします。

その探索方向に対して、制約がさらに満たされることを保証する線形探索が行われます。

# 入力

  * `M`: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: f の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ を `(M, p) -> X` または `(M, X, p) -> X` としてインプレースで計算する関数
  * `Hess_f`: f の (リーマン) ヘッセ行列 $\operatorname{Hess}f: T_{p}\mathcal M → T_{p}\mathcal M$ を `(M, p, X) -> Y` または `(M, Y, p, X) -> Y` としてインプレースで計算する関数
  * `p`: 多様体 $\mathcal M$ 上の点

または、`f`、`grad_f`、`Hess_f`、および制約を含む [`ConstrainedManifoldObjective`](@ref) `cmo`

# キーワード引数

制約に関連するキーワード引数（最初の11個）は、[`ConstrainedManifoldObjective`](@ref) `cmo` を渡すと無視されます。

  * `centrality_condition=missing`; ステップサイズを受け入れる際の追加条件。これを使用して、結果の反復点が内部点であることを保証できます。チェック `(N,q) -> true/false` を提供する場合、ここで `N` は `step_problem` の多様体です。
  * `equality_constraints=nothing`: 等式制約の数 $n$。
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、結果を割り当てるか（[`AllocatingEvaluation`](@ref)）または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目の引数です。
  * `g=nothing`: 不等式制約
  * `grad_g=nothing`: 不等式制約の勾配
  * `grad_h=nothing`: 等式制約の勾配
  * `gradient_range=nothing`: 勾配がどのように表現されるかを指定します。`nothing` は [`NestedPowerRepresentation`](@extref `ManifoldsBase.NestedPowerRepresentation`) と同等です。
  * `gradient_equality_range=gradient_range`: 等式制約の勾配がどのように表現されるかを指定します。
  * `gradient_inequality_range=gradient_range`: 不等式制約の勾配がどのように表現されるかを指定します。
  * `h=nothing`: 等式制約
  * `Hess_g=nothing`: 不等式制約のヘッセ行列
  * `Hess_h=nothing`: 等式制約のヘッセ行列
  * `inequality_constraints=nothing`: 不等式制約の数 $m$。
  * `λ=ones(length(h(M, p)))`: 等式制約 $h$ に関するラグランジュ乗数
  * `μ=ones(length(g(M, p)))`: 不等式制約 $g$ に関するラグランジュ乗数
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション $\operatorname{retr}$、リトラクションに関するセクションを参照してください（@extref ManifoldsBase :doc:`retractions`）。
  * `ρ=μ's / length(μ)`: バリアパラメータ `β` をサブ問題で計算するために、直交性 `μ's/m` を保存します。
  * `s=copy(μ)`: スラック変数の初期値
  * `σ=`[`calculate_σ`](@ref)`(M, cmo, p, μ, λ, s)`: サブ問題でのバリアパラメータ `β` のスケーリングファクターで、反復中に更新されます。
  * `step_objective`: KKTベクトル場のノルム [`KKTVectorFieldNormSq`](@ref) とその勾配 [`KKTVectorFieldNormSqGradient`](@ref) の [`ManifoldGradientObjective`](@ref)
  * `step_problem`: 多様体 $\mathcal M × ℝ^m × ℝ^n × ℝ^m$ と `step_objective` を組み合わせたもので、`stepsize=` がステップサイズを決定するために使用する問題
  * `step_state`: 点と探索方向を持つ [`StepsizeState`](@ref)
  * `stepsize=`[`ArmijoLinesearch`](@ref)`()`: ステップを受け入れるための追加基準として `centrality_condtion` キーワードを持つステップサイズを決定するためのファンクタ
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenKKTResidualLess`](@ref)`(1e-8)`: 停止基準が満たされることを示すファンクタ。デフォルトでは KKTベクトル場の残差または最大ステップ数に依存し、どちらか早く達成されます。
  * `sub_kwargs=(;)`: サブオプションのデコレータ用のキーワード引数。デバッグなど、メインソルバーのデバッグオプション（サブサンプリングなど）を自動的に尊重します。
  * `sub_objective`: サブソルバーで使用する方程式系をモデル化する [`SymmetricLinearSystemObjective`](@ref)。これは、解決を目指す $\mathcal A(X) + b = 0$ の中の [`CondensedKKTVectorFieldJacobian`](@ref) $\mathcal A(X)$ と [`CondensedKKTVectorField`](@ref) $b$ を含みます。これは `sub_problem=` キーワードを定義するために使用され、`sub_problem` を直接設定した場合は効果がありません。
  * `sub_stopping_criterion=`[`StopAfterIteration`](@ref)`(manifold_dimension(M))`[`|`](@ref StopWhenAny)[`StopWhenRelativeResidualLess`](@ref)`(c,1e-8)`, ここで $c = \lVert b \rVert_{}$ は解決すべきシステムからのものです。これは `sub_state=` キーワードを定義するために使用され、`sub_state` を直接設定した場合は効果がありません。
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M, sub_objective)`: ソルバー用の問題または閉形式の解関数を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `sub_state=`[`ConjugateResidualState`](@ref): 使用するサブソルバーを指定する状態。閉形式の解の場合、これは関数のタイプを示します。
  * `vector_space=`[`Rn`](@ref Manopt.Rn) 整数を与えると、ベクトル空間成分 $ℝ^m,ℝ^n$ に使用される多様体を返す関数。
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M,p)`: `p` に関する初期勾配。
  * `Y=zero(μ)`:  $\mu$ に関する初期勾配
  * `Z=zero(λ)`:  $\lambda$ に関する初期勾配
  * `W=zero(s)`:  $s$ に関する初期勾配

これらのキーワードを設定するために使用される内部キーワード `_step_M`、`_step_p`、`_sub_M`、`_sub_p`、および `_sub_X` も変更しないでください。

他のすべてのキーワード引数は、状態デコレータ用の [`decorate_state!`](@ref) または目的用の [`decorate_objective!`](@ref) に渡されます。

!!! note
    `centrality_condition=mising` は、線形探索中の中心性のチェックを無効にしますが、[`InteriorPointCentralityCondition`](@ref)`(cmo, γ)` を渡すことで、このチェックを有効にすることができます。ここで `γ` は定数です。


# 出力

得られた近似制約最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、[`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードに注意してください。 ```
