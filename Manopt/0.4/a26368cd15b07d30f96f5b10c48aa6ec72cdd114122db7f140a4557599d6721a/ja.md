```
interior_point_Newton(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
interior_point_Newton(M, cmo::ConstrainedManifoldObjective, p=rand(M); kwargs...)
interior_point_Newton!(M, f, grad_f, Hess_f, p; kwargs...)
interior_point_Newton(M, ConstrainedManifoldObjective, p; kwargs...)
```

[LaiYoshise:2024](@cite) に従って、内部点ニュートン法を実行します。

制約付き問題を解決するために

$$
\begin{aligned}
\min_{p ∈\mathcal{M}} &f(p)\\
\text{subject to } &g_i(p)\leq 0 \quad \text{ for } i= 1, …, m,\\
\quad &h_j(p)=0 \quad \text{ for } j=1,…,n,
\end{aligned}
$$

このアルゴリズムは、スラック変数 `s` を用いて KKT 系を拡張することに基づいて線形システムを反復的に解決します。

$$
\operatorname{J} F(p, μ, λ, s)[X, Y, Z, W] = -F(p, μ, λ, s),
\text{ where }
X ∈ T_p\mathcal M, Y,W ∈ ℝ^m, Z ∈ ℝ^n,
$$

縮約形については、[`CondensedKKTVectorFieldJacobian`](@ref) と [`CondensedKKTVectorField`](@ref) をそれぞれ参照してください。通常、これが解かれる形です。得られた縮約形の `X` と `Z` から、他の二つ、$Y$、$W$ が計算されます。

現在の反復点 $(p, μ, λ, s)$ における勾配 $(X,Y,Z,W)$ から、KKT ベクトル場のノルム（平方）[`KKTVectorFieldNormSq`](@ref) とその勾配 [`KKTVectorFieldNormSqGradient`](@ref) を用いて線形探索が行われ、[`InteriorPointCentralityCondition`](@ref) と共に使用されます。

ベクトル場 $F$ には制約関数 $g, h$ の勾配が含まれているため、その勾配またはヤコビアンは制約のヘッセ行列を必要とします。

その探索方向に対して、制約がさらに満たされることを保証する線形探索が行われます。

# 入力

  * `M`:      多様体 $\mathcal M$
  * `f`:      最小化するコスト関数 $f : \mathcal M → ℝ$
  * `grad_f`: $f$ の勾配 $\operatorname{grad} f : \mathcal M → T \mathcal M$
  * `Hess_f`: ヘッセ行列 $\operatorname{Hess}f(p): T_p\mathcal M → T_p\mathcal M$, $X ↦ \operatorname{Hess}f(p)[X] = ∇_X\operatorname{grad}f(p)$
  * `p=`[`rand`](@extref Base.rand-Tuple{AbstractManifold})`(M)`: 初期値 $p  ∈  \mathcal M$

または、`f`、`grad_f`、`Hess_f`、および制約を含む [`ConstrainedManifoldObjective`](@ref) `cmo`

# キーワード引数

制約に関連するキーワード引数（最初の11個）は、[`ConstrainedManifoldObjective`](@ref) `cmo` を渡すと無視されます。

  * `centrality_condition=missing`; ステップサイズを受け入れる際の追加条件。これを使用して、結果の反復点が内部点であることを保証できます。チェック `(N,q) -> true/false` を提供する場合、ここで `N` は `step_problem` の多様体です。
  * `equality_constraints=nothing`: 等式制約の数 $n$。
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることで動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を修正してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は二番目になります。
  * `g=nothing`: 不等式制約
  * `grad_g=nothing`: 不等式制約の勾配
  * `grad_h=nothing`: 等式制約の勾配
  * `gradient_range=nothing`: 勾配がどのように表現されるかを指定します。`nothing` は [`NestedPowerRepresentation`](@extref) と同等です。
  * `gradient_equality_range=gradient_range`: 等式制約の勾配がどのように表現されるかを指定します。
  * `gradient_inequality_range=gradient_range`: 不等式制約の勾配がどのように表現されるかを指定します。
  * `h=nothing`: 等式制約
  * `Hess_g=nothing`: 不等式制約のヘッセ行列
  * `Hess_h=nothing`: 等式制約のヘッセ行列
  * `inequality_constraints=nothing`: 不等式制約の数 $m$。
  * `λ=ones(length(h(M, p)))`: 等式制約 $h$ に関するラグランジュ乗数
  * `μ=ones(length(g(M, p)))`: 不等式制約 $g$ に関するラグランジュ乗数
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するリトラクション。デフォルトでは、選択された `p` の表現に関して `M` のデフォルトセットに従います。
  * `ρ=μ's / length(μ)`: バリアパラメータ `β` をサブ問題で計算するために、直交性 `μ's/m` を保存します。
  * `s=copy(μ)`: スラック変数の初期値
  * `σ=`[`calculate_σ`](@ref)`(M, cmo, p, μ, λ, s)`: サブ問題でのバリアパラメータ `β` のスケーリングファクターで、反復中に更新されます。
  * `step_objective`: KKT ベクトル場のノルム [`KKTVectorFieldNormSq`](@ref) とその勾配 [`KKTVectorFieldNormSqGradient`](@ref) の [`ManifoldGradientObjective`](@ref)
  * `step_problem`: 多様体 $\mathcal M × ℝ^m × ℝ^n × ℝ^m$ と `step_objective` を組み合わせたもので、線形探索 `stepsize=` がステップサイズを決定するために使用する問題です。
  * `step_state`: 点と探索方向を持つ [`StepsizeState`](@ref)
  * `stepsize` は、ステップを受け入れるための追加条件として [`InteriorPointCentralityCondition`](@ref) を持つ [`ArmijoLinesearch`](@ref) です。このステップサイズは独自の `step_problem` と `step_state` で動作します。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(200)`[`|`](@ref StopWhenAny)[`StopWhenKKTResidualLess`](@ref)`(1e-8)`: 停止基準。デフォルトでは KKT ベクトル場の残差または最大ステップ数に依存し、どちらか早く達成されます。
  * `sub_kwargs=(;)`: サブオプションのデコレータとして使用されるキーワード引数。デバッグなど、メインソルバーのデバッグオプション（サブサンプリングなど）を自動的に尊重します。
  * `sub_objective`: サブソルバーで使用する方程式系をモデル化する [`SymmetricLinearSystemObjective`](@ref)。これは、解決を目指す $\mathcal A(X) + b = 0$ の中の [`CondensedKKTVectorFieldJacobian`](@ref) $\mathcal A(X)$ と [`CondensedKKTVectorField`](@ref) $b$ を含みます。これを使用して `sub_problem` を設定します。`sub_problem` を直接設定した場合、このキーワードは効果がありません。
  * `sub_stopping_criterion=`[`StopAfterIteration`](@ref)`(manifold_dimension(M))`[`|`](@ref StopWhenAny)[`StopWhenRelativeResidualLess`](@ref)`(c,1e-8)`, ここで $c = \lVert b \rVert$ は解決すべきシステムからのものです。このキーワードは `sub_state` で使用されます。このキーワードを直接設定した場合、このキーワードは効果がありません。
  * `sub_problem`: `sub_objective` と $(p,λ)$ の接空間を組み合わせて多様体 $\mathcal M × ℝ^n$ の問題にします。これはサブソルバーのための多様体と目的です。
  * `sub_state=`[`ConjugateResidualState`](@ref): サブソルバーを指定する状態。このデフォルトは `sub_kwargs...` で装飾されています。
  * `vector_space=`[`Rn`](@ref Manopt.Rn) は、整数を与えると、ベクトル空間成分 $ℝ^m,ℝ^n$ に使用される多様体を返す関数です。
  * `X=`[`zero_vector`](@extref `ManifoldsBase.zero_vector-Tuple{AbstractManifold, Any}`)`(M,p)`: `p` に関する初期勾配。
  * `Y=zero(μ)`:  $\mu$ に関する初期勾配
  * `Z=zero(λ)`:  $\lambda$ に関する初期勾配
  * `W=zero(s)`:  $s$ に関する初期勾配

また、これらのキーワードを設定するために使用される内部キーワード `_step_M`、`_step_p`、`_sub_M`、`_sub_p`、および `_sub_X` も変更しないでください。

他のすべてのキーワード引数は、状態デコレータのために [`decorate_state!`](@ref) に、目的のために [`decorate_objective!`](@ref) に渡されます。

!!! note
    `centrality_condition=mising` は、線形探索中の中心性チェックを無効にしますが、[`InteriorPointCentralityCondition`](@ref)`(cmo, γ)` を渡すことで、このチェックを有効にすることができます。ここで `γ` は定数です。


# 出力

得られた近似制約最小化点 $p^*$。ソルバーの全体的な最終状態を取得するには、[`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードに注意してください。 ```
