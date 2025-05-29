```
ApproxHessianBFGS{E, P, G, T, B<:AbstractBasis{ℝ}, VTR, R<:Real} <: AbstractApproxHessian
```

BFGS更新によってヘッセ行列を近似するファンクタ。

# フィールド

  * `gradient!!` 勾配関数（アロケーションまたはミューテーションのいずれか、`evaluation`パラメータを参照）。
  * `scale`
  * `vector_transport_method` 使用するベクトル輸送。

## 内部一時フィールド

  * `p_tmp` 現在の点`p`の一時ストレージ。
  * `grad_tmp` 現在の`p`での勾配の一時ストレージ。
  * `matrix` 近似演算子の行列表現の一時ストレージ。
  * `basis` 現在の`p`での直交基底の一時ストレージ。

# コンストラクタ

```
ApproxHessianBFGS(M, p, gradF; kwargs...)
```

## キーワード引数

  * `initial_operator` （`Matrix{Float64}(I, manifold_dimension(M), manifold_dimension(M))`）初期近似演算子の行列表現。
  * `basis` （`DefaultOrthonormalBasis()`）初期反復点`p`の接空間における直交基底。
  * `nu` （`-1`）
  * `evaluation` （[`AllocatingEvaluation`](@ref)）勾配がアロケーション関数として与えられるか、インプレース（[`InplaceEvaluation`](@ref)）として与えられるか。
  * `vector_transport_method` （`ParallelTransport()`）使用するベクトル輸送$\mathcal T_{\cdot\gets\cdot}$。
