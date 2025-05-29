```
ApproxHessianFiniteDifference{E, P, T, G, RTR, VTR, R <: Real} <: AbstractApproxHessian
```

勾配評価の有限差分によってヘッセ行列を近似するファンクタ。

点 `p` と方向 `X` および関数 $F$ の勾配 $\operatorname{grad}F: \mathcal M → T\mathcal M$ が与えられたとき、ヘッセ行列は次のように近似されます。$c$ をステップサイズ、$X∈ T_p\mathcal M$ を接ベクトルとし、$q = \operatorname{retr}_p(\frac{c}{\lVert X \rVert_p}X)$ を再収縮に従った長さ $c$ の方向 $X$ へのステップとします。次に、ヘッセ行列は勾配の有限差分によって近似され、ここで $\mathcal T_{\cdot\gets\cdot}$ はベクトル輸送です。

$$
\operatorname{Hess}F(p)[X] ≈
\frac{\lVert X \rVert_p}{c}\Bigl(
  \mathcal T_{p\gets q}\bigr(\operatorname{grad}F(q)\bigl) - \operatorname{grad}F(p)
\Bigl)
$$

# フィールド

  * `gradient!!`:              勾配関数（割り当てまたは変更のいずれか、`evaluation` パラメータを参照）
  * `step_length`:             有限差分のためのステップ長
  * `retraction_method`:       使用する再収縮
  * `vector_transport_method`: 使用するベクトル輸送

## 内部一時フィールド

  * `grad_tmp`:     現在の `p` における勾配の一時保存
  * `grad_dir_tmp`: 現在の `p_dir` における勾配の一時保存
  * `p_dir::P`:     前方方向への一時保存（または式中の $q$）

# コンストラクタ

```
ApproximateFiniteDifference(M, p, grad_f; kwargs...)
```

## キーワード引数

  * `evaluation`:              ([`AllocatingEvaluation`](@ref)) 勾配が割り当て関数として与えられるか、インプレースであるか（[`InplaceEvaluation`](@ref)）。
  * `steplength`:              ($2^{-14}$) 勾配評価を近似するためのステップ長 $c$
  * `retraction_method`:       (`default_retraction_method(M, typeof(p))`) 近似に使用する `retraction(M, p, X)`。
  * `vector_transport_method`: (`default_vector_transport_method(M, typeof(p))`) 使用するベクトル輸送
