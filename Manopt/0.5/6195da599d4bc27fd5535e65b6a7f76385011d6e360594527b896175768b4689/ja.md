```
ApproxHessianFiniteDifference{E, P, T, G, RTR, VTR, R <: Real} <: AbstractApproxHessian
```

勾配評価の有限差分によってヘッセ行列を近似するファンクタ。

点 `p` と方向 `X` および関数 $f$ の勾配 $\operatorname{grad} f(p)$ が与えられたとき、ヘッセ行列は次のように近似されます：$c$ をステップサイズ、$X ∈ T_{p}\mathcal M$ を接ベクトルとし、$q = \operatorname{retr}_p(\frac{c}{\lVert X \rVert_p}X)$ を再収束に従った長さ $c$ の方向 $X$ へのステップとします。次に、ヘッセ行列は勾配の有限差分によって近似され、ここで $\mathcal T_{⋅←⋅}$ はベクトル輸送です。

$$
\operatorname{Hess}f(p)[X] ≈
\frac{\lVert X \rVert_p}{c}\Bigl(
  \mathcal T_{p\gets q}\bigr(\operatorname{grad}f(q)\bigl) - \operatorname{grad}f(p)
\Bigl)
$$

# フィールド

  * `gradient!!`:              勾配関数（割り当てまたは変更のいずれか、`evaluation` パラメータを参照）
  * `step_length`:             有限差分のためのステップ長
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束 $\operatorname{retr}$、[再収束に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)を参照

## 内部一時フィールド

  * `grad_tmp`:     現在の `p` における勾配の一時保存
  * `grad_dir_tmp`: 現在の `p_dir` における勾配の一時保存
  * `p_dir::P`:     前方方向への一時保存（または式中の $q$）

# コンストラクタ

```
ApproximateFiniteDifference(M, p, grad_f; kwargs...)
```

## キーワード引数

  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルがその結果を割り当てるか（[`AllocatingEvaluation`](@ref)）、または入力引数を変更してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、変更された引数は2番目のものです。
  * `steplength=`2^{-14}$: 勾配評価を近似するためのステップ長$c``
  * `retraction_method=`[`default_retraction_method`](@extref `ManifoldsBase.default_retraction_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用する再収束 $\operatorname{retr}$、[再収束に関するセクション](@extref ManifoldsBase :doc:`retractions`)を参照
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、[ベクトル輸送に関するセクション](@extref ManifoldsBase :doc:`vector_transports`)

```
