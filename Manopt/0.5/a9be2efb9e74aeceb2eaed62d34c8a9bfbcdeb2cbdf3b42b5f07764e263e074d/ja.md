```
ApproxHessianSymmetricRankOne{E, P, G, T, B<:AbstractBasis{ℝ}, VTR, R<:Real} <: AbstractApproxHessian
```

ヘッセ行列を対称ランク1更新によって近似するファンクタ。

# フィールド

  * `gradient!!`: 勾配関数（割り当てまたは変更のいずれか、`evaluation`パラメータを参照）。
  * `ν`: 更新の分母があまり小さくならないようにするための小さな実数で、したがってメソッドが崩壊しないようにする。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、ベクトル輸送に関する[セクション](@extref ManifoldsBase :doc:`vector_transports`)を参照。

## 内部一時フィールド

  * `p_tmp`: 現在の点 `p` の一時ストレージ。
  * `grad_tmp`: 現在の `p` における勾配の一時ストレージ。
  * `matrix`: 近似演算子の行列表現の一時ストレージ。
  * `basis`: 現在の `p` における直交基底の一時ストレージ。

# コンストラクタ

```
ApproxHessianSymmetricRankOne(M, p, gradF; kwargs...)
```

## キーワード引数

  * `initial_operator` (`Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M))`) 初期近似演算子の行列表現。
  * `basis` (`DefaultOrthonormalBasis()`) 初期反復点 `p` の接空間における直交基底。
  * `nu` (`-1`)
  * `evaluation=`[`AllocatingEvaluation`](@ref)`()`: 配列を返す関数、例えば点や接ベクトルが、その結果を割り当てることによって動作するか（[`AllocatingEvaluation`](@ref)）、または入力引数を変更してその中で結果を返すか（[`InplaceEvaluation`](@ref)）を指定します。通常、最初の引数は多様体であり、変更された引数は2番目の引数です。
  * `vector_transport_method=`[`default_vector_transport_method`](@extref `ManifoldsBase.default_vector_transport_method-Tuple{AbstractManifold}`)`(M, typeof(p))`: 使用するベクトル輸送 $\mathcal T_{⋅←⋅}$、ベクトル輸送に関する[セクション](@extref ManifoldsBase :doc:`vector_transports`)を参照。
