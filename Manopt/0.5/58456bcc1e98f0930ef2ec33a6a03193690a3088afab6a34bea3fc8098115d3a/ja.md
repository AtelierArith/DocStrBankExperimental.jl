```
trust_regions(M, f, grad_f, Hess_f, p=rand(M); kwargs...)
trust_regions(M, f, grad_f, p=rand(M); kwargs...)
trust_regions!(M, f, grad_f, Hess_f, p; kwargs...)
trust_regions!(M, f, grad_f, p; kwargs...)
```

リーマン信頼領域ソルバーを実行して、マニフォールド上で `f` を最小化します。詳細は [AbsilBakerGallivan:2006, ConnGouldToint:2000](@cite) を参照してください。

ヘッセ行列が提供されていない場合、ヘッセ行列は有限差分を使用して計算されます。詳細は [`ApproxHessianFiniteDifference`](@ref) を参照してください。更新ベクトルを見つけるための内部信頼領域サブプロブレムを解決するために、デフォルトでは [`truncated_conjugate_gradient_descent`](@ref) が使用されます。

# 入力

  * `M::`[`AbstractManifold`](@extref `ManifoldsBase.AbstractManifold`)``: リーマン多様体 $\mathcal M$
  * `f`: コスト関数 $f: \mathcal M→ ℝ$ を `(M, p) -> v` として実装
  * `grad_f`: f の (リーマン) 勾配 $\operatorname{grad}f: \mathcal M → T_{p}\mathcal M$ を `(M, p) -> X` または `(M, X, p) -> X` として計算する関数
  * `Hess_f`: f の (リーマン) ヘッセ行列 $\operatorname{Hess}f: T_{p}\mathcal M → T_{p}\mathcal M$ を `(M, p, X) -> Y` または `(M, Y, p, X) -> Y` として計算する関数
  * `p`: 多様体 $\mathcal M$ 上の点

# キーワード引数

  * `acceptance_rate`:        受け入れ/拒否の閾値: ρ（反復の性能比）が受け入れ率 ρ' 以上であれば、候補が受け入れられます。この値は $0$ と $rac{1}{4}$ の間である必要があります。
  * `augmentation_threshold=0.75`: 信頼領域の拡張閾値: ρ がこの閾値を超える場合、解は信頼領域の境界上にあり、負の曲率があり、半径が拡張されます（増加します）。
  * `augmentation_factor=2.0`: 信頼領域の拡張係数
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、結果を割り当てる方法（[`AllocatingEvaluation`](@ref)）で動作するか、入力引数を修正してその中で結果を返す方法（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、修正された引数は2番目の引数です。
  * `κ=0.1`: tCG メソッド [`truncated_conjugate_gradient_descent`](@ref) の線形収束目標率であり、停止基準に使用されます。
  * `max_trust_region_radius`: 最大信頼領域半径
  * `preconditioner`:       ヘッセ行列 H の前処理器。これは、割り当て関数 `(M, p, X) -> Y` またはインプレース関数 `(M, Y, p, X) -> Y` であり、`evaluation` を参照し、デフォルトでは単位行列に設定されています。
  * `project!=copyto!`: 数値的安定性のために、各反復後に接空間に投影することが可能です。この関数は `Y` のインプレースで動作する必要があります。すなわち、`(M, Y, p, X) -> Y` であり、`X` と `Y` は同じメモリを使用できます。
  * `randomize=false`:      `X` がランダムベクトルで初期化されるかどうかを示します。これにより前処理が無効になります。
  * `ρ_regularization=1e3`: 数値的不正確さを避けるために性能評価 $ρ$ を正則化します。
  * `reduction_factor=0.25`: 信頼領域の削減係数
  * `reduction_threshold=0.1`: 信頼領域の削減閾値: ρ がこの閾値を下回る場合、信頼領域半径は `reduction_factor` によって削減されます。
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する引き戻し $\operatorname{retr}$ を指定します。詳細は [引き戻しに関するセクション](@extref ManifoldsBase :doc:`retractions`) を参照してください。
  * `stopping_criterion=`[`StopAfterIteration`](@ref)`(1000)`[`|`](@ref StopWhenAny)[`StopWhenGradientNormLess`](@ref)`(1e-6)`: 停止基準が満たされていることを示すファンクタ
  * `sub_kwargs=``(;)`: サブソルバーの目的の [`decorate_objective!`](@ref)、サブソルバーの状態の [`decorate_state!`](@ref)、およびサブ状態コンストラクタ自体に渡されるキーワード引数の名前付きタプル。
  * `sub_stopping_criterion=`( [`truncated_conjugate_gradient_descent`](@ref) を参照): 停止基準が満たされていることを示すファンクタ
  * `sub_problem=`[`DefaultManoptProblem`](@ref)`(M,`[`ConstrainedManifoldObjective`](@ref)`(subcost, subgrad; evaluation=evaluation))`: ソルバーの問題または閉じた形式の解関数を指定します。これは割り当て可能またはインプレースである可能性があります。
  * `sub_state=`[`QuasiNewtonState`](@ref): 使用するサブソルバーを指定する状態。閉じた形式の解の場合、これは関数のタイプを示します。ここで [`QuasiNewtonLimitedMemoryDirectionUpdate`](@ref) と [`InverseBFGS`](@ref) が使用されます。
  * `θ=1.0`:                tCG メソッド [`truncated_conjugate_gradient_descent`](@ref) の $1+θ$ の超線形収束目標率であり、停止基準に使用されます。
  * `trust_region_radius=`[`injectivity_radius`](@extref `ManifoldsBase.injectivity_radius-Tuple{AbstractManifold}`)`(M) / 4`: 初期信頼領域半径

ヘッセ行列が提供されていない場合、ヘッセ行列は有限差分を使用して計算されます。詳細は [`ApproxHessianFiniteDifference`](@ref) を参照してください。

他のすべてのキーワード引数は、状態デコレーターのための [`decorate_state!`](@ref) または目的デコレーターのための [`decorate_objective!`](@ref) に渡されます。

# 出力

得られた近似最小化点 $p^*$。ソルバーの最終状態全体を取得するには、詳細については [`get_solver_return`](@ref) を参照してください。特に `return_state=` キーワードを参照してください。

# 参照

[`truncated_conjugate_gradient_descent`](@ref) ```
