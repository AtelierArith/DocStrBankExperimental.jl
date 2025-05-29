```
trust_regions(M, f, grad_f, hess_f, p=rand(M))
trust_regions(M, f, grad_f, p=rand(M))
```

リーマニアン信頼領域ソルバーを使用して、マンフォールド上で最適化を行い、`f`を最小化します。詳細は[AbsilBakerGallivan:2006, ConnGouldToint:2000](@cite)を参照してください。

ヘッセ行列が提供されていない場合、ヘッセ行列は有限差分を使用して計算されます。詳細は[`ApproxHessianFiniteDifference`](@ref)を参照してください。更新ベクトルを見つけるための内部信頼領域サブプロブレムを解くために、デフォルトでは[`truncated_conjugate_gradient_descent`](@ref)が使用されます。

# 入力

  * `M`:      マンフォールド $\mathcal M$
  * `f`:      最小化するコスト関数 $f : \mathcal M → ℝ$
  * `grad_f`: 関数 $F$ の勾配 $\operatorname{grad}F : \mathcal M → T \mathcal M$
  * `Hess_f`: （オプション）ヘッセ行列 $\operatorname{Hess}F(x): T_x\mathcal M → T_x\mathcal M$, $X ↦ \operatorname{Hess}F(x)[X] = ∇_ξ\operatorname{grad}f(x)$
  * `p`:      （`rand(M)`）初期値 $x  ∈  \mathcal M$

# キーワード引数

  * `acceptance_rate`:        受け入れ/拒否の閾値：もし ρ（反復の性能比）が受け入れ率 ρ' 以上であれば、候補が受け入れられます。この値は $0$ と $\frac{1}{4}$ の間であるべきです。
  * `augmentation_threshold`: （`0.75`）信頼領域の拡張閾値：もし ρ がこの閾値より大きい場合、解は信頼領域の境界上にあり、負の曲率があり、半径が拡張（増加）されます。
  * `augmentation_factor`:    （`2.0`）信頼領域の拡張係数
  * `evaluation`:             （[`AllocatingEvaluation`](@ref)）勾配とヘッセ行列が割り当てによって動作するか（デフォルト）または[`InplaceEvaluation`](@ref)でインプレースで動作するかを指定します。
  * `κ`:                      （`0.1`）tCG法の線形収束目標率 [`truncated_conjugate_gradient_descent`](@ref)であり、そこでの停止基準に使用されます。
  * `max_trust_region_radius`: 最大信頼領域半径
  * `preconditioner`:          ヘッセ行列の逆を近似するべき対称正定値演算子である前処理器
  * `project!`;               （`copyto!`）数値的安定性のためにサブソルバー内で接ベクトルの射影操作を指定します。必要な形式は `(M, Y, p, X) -> ...` で、`Y`のインプレースで動作します。
  * `randomize`;              信頼領域の解法をランダムな接ベクトルで開始し、前処理器を使用しない場合はtrueに設定します。
  * `ρ_regularization`:       （`1e3`）数値的不正確さを避けるために性能評価 $ρ$ を正則化します。
  * `reduction_factor`:       （`0.25`）信頼領域の削減係数
  * `reduction_threshold`:    （`0.1`）信頼領域の削減閾値：もし ρ がこの閾値未満であれば、信頼領域半径は `reduction_factor` によって削減されます。
  * `retraction` （`default_retraction_method(M, typeof(p))`）使用する引き戻し
  * `stopping_criterion`:     （[`StopAfterIteration`](@ref)`(1000) |`[`StopWhenGradientNormLess`](@ref)`(1e-6)`) 停止基準を示す[`StoppingCriterion`](@ref)から継承されたファンクタ。
  * `sub_kwargs`:             サブ状態に渡され、サブオプションを装飾するために使用されるキーワード引数
  * `sub_stopping_criterion`: サブソルバーの停止基準、TCGと同じ基準を使用します。
  * `sub_problem`:            （[`DefaultManoptProblem`](@ref)`(M,`[`ConstrainedManifoldObjective`](@ref)`(subcost, subgrad; evaluation=evaluation))`) サブソルバーの問題
  * `sub_state`:              （[`QuasiNewtonState`](@ref)）[`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref)を使用し、[`InverseBFGS`](@ref)と`sub_stopping_criterion`を停止基準として使用します。`sub_kwargs`も参照してください。
  * `θ`:                      （`1.0`）1+θはtCG法の超線形収束目標率 [`truncated_conjugate_gradient_descent`](@ref)であり、そこでの停止基準に使用されます。
  * `trust_region_radius`:     初期信頼領域半径

ヘッセ行列が提供されていない場合、ヘッセ行列は有限差分を使用して計算されます。詳細は[`ApproxHessianFiniteDifference`](@ref)を参照してください。

# 出力

得られた（近似的な）最小値 $p^*$、詳細は[`get_solver_return`](@ref)を参照してください。

# 参照

[`truncated_conjugate_gradient_descent`](@ref) ```
