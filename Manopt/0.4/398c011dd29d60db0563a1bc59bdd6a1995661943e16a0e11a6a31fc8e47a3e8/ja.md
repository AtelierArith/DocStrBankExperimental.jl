```
convex_bundle_method(M, f, ∂f, p)
```

凸バンドル法を実行します $p_{j+1} = \mathrm{retr}(p_k, -g_k)$、ここで $\mathrm{retr}$ はリトラクションであり、

$$
g_k = \sum_{j\in J_k} λ_j^k \mathrm{P}_{p_k←q_j}X_{q_j},
$$

$$
p_k
$$

は最後の真剣な反復、$X_{q_j} ∈ ∂f(q_j)$ であり、$λ_j^k$ は [`convex_bundle_method_subsolver`](@ref) によって提供される二次サブ問題の解です。

サブ微分は集合値である可能性がありますが、引数 `∂f` は常にサブ微分から1つの要素を返すべきですが、必ずしも決定論的ではありません。

詳細については、[BergmannHerzogJasa:2024](@cite) を参照してください。

# 入力

  * `M`:  多様体 $\mathcal M$
  * `f`:   最小化するコスト関数 $f:\mathcal M→ℝ$
  * `∂f`: サブグラディエント $∂f: \mathcal M → T\mathcal M$ は、常にサブ微分から1つの値/要素のみを返すように制限されています。この関数は、割り当て関数 `(M, p) -> X` または変異関数 `(M, X, p) -> X` として渡すことができ、`evaluation` を参照してください。
  * `p`:  （`rand(M)`）初期値 $p_0 ∈ \mathcal M$

# オプション

  * `atol_λ`:                    （`eps()`）λの凸係数に対する許容パラメータ。
  * `atol_errors`:               （`eps()`）線形化誤差に対する許容パラメータ。
  * `m`:                         （`1e-3`）コストの減少をテストするためのパラメータ: $f(q_{k+1}) \le f(p_k) + m \xi$。
  * `diameter`:                  （`50.0`）出発点での目的関数のレベルセットの直径の推定。
  * `domain`:                    （`(M, p) -> isfinite(f(M, p))`）現在の候補が目的 `f` の定義域にあるときに真を返し、そうでない場合は偽を返す関数、例えば domain = (M, p) -> p ∈ dom f(M, p) ? true : false。
  * `k_max`:                     多様体の断面曲率の上限。
  * `evaluation`:                （[`AllocatingEvaluation`](@ref)）サブグラディエントが割り当て（デフォルト）形式 `∂f(M, q)` で動作するか、または [`InplaceEvaluation`](@ref) の形で動作するかを指定します。すなわち、`∂f!(M, X, p)` の形です。
  * `inverse_retraction_method`: （`default_inverse_retraction_method(M, typeof(p))`）使用する逆リトラクション法
  * `retraction_method`:         （`default_retraction_method(M, typeof(p))`）使用する `retraction(M, p, X)`。
  * `stopping_criterion`:        （[`StopWhenLagrangeMultiplierLess`](@ref)`(1e-8; names=["-ξ"])`）停止するタイミングを示すファンクタ、[`StoppingCriterion`](@ref) を参照してください。
  * `vector_transport_method`:   （`default_vector_transport_method(M, typeof(p))`）使用するベクトル輸送法
  * `sub_problem`:               最後の真剣な反復 `p_last_serious`、線形化誤差 `linearization_errors`、および輸送されたサブグラディエント `transported_subgradients` を考慮して、`M` 上のサブ問題を解決する新しい割り当てを伴う関数

# 出力

得られた（近似的な）最小化点 $p^*$、詳細については [`get_solver_return`](@ref) を参照してください。
