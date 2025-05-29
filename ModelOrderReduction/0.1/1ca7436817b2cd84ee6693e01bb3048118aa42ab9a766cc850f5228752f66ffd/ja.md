```julia
deim(
    full_vars,
    linear_coeffs,
    constant_part,
    nonlinear_part,
    reduced_vars,
    linear_projection_matrix,
    nonlinear_projection_matrix;
    kwargs...
)

```

離散経験的補間法（DEIM）を適用して縮小モデルを計算します。

この方法では、ユーザーが自分の選択した投影行列を入力することができます。

従属変数 $\mathbf y\in\mathbb R^n$ のための投影行列 $V\in\mathbb R^{n\times k}$ と非線形関数 $\mathbf F\in\mathbb R^n$ のための投影行列 $U\in\mathbb R^{n\times m}$ が与えられたとき、フルオーダーモデル（FOM）

$$
\frac{d}{dt}\mathbf y(t)=A\mathbf y(t)+\mathbf g(t)+\mathbf F(\mathbf y(t))
$$

は縮小オーダーモデル（ROM）

$$
\frac{d}{dt}\hat{\mathbf y}(t)=\underbrace{V^TAV}_{k\times k}\hat{\mathbf y}(t)+V^T
\mathbf g(t)+\underbrace{V^TU(P^TU)^{-1}}_{k\times m}\underbrace{P^T\mathbf F(V
\hat{\mathbf y}(t))}_{m\times1}
$$

に変換されます。

ここで、$P=[\mathbf e_{\rho_1},\dots,\mathbf e_{\rho_m}]\in\mathbb R^{n\times m}$、$\rho_1,\dots,\rho_m$ はDEIMポイント選択アルゴリズムからの補間インデックスであり、$\mathbf e_{\rho_i}=[0,\ldots,0,1,0,\ldots,0]^T\in\mathbb R^n$ は単位行列 $I_n\in\mathbb R^{n\times n}$ の $\rho_i$-列目です。

# 引数

  * `full_vars::AbstractVector`: FOMにおける従属変数 $\underset{n\times 1}{\mathbf y}$。
  * `linear_coeffs::AbstractMatrix`: FOMにおける線形項の係数行列 $\underset{n\times n}A$。
  * `constant_part::AbstractVector`: FOMにおける定数項 $\underset{n\times 1}{\mathbf g}$。
  * `nonlinear_part::AbstractVector`: FOMにおける非線形関数 $\underset{n\times 1}{\mathbf F}$。
  * `reduced_vars::AbstractVector`: 縮小オーダーモデルにおける従属変数 $\underset{k\times 1}{\hat{\mathbf y}}$。
  * `linear_projection_matrix::AbstractMatrix`: 従属変数 $\mathbf y$ のための投影行列 $\underset{n\times k}V$。
  * `nonlinear_projection_matrix::AbstractMatrix`: 非線形関数 $\mathbf F$ のための投影行列 $\underset{n\times m}U$。

# 戻り値

  * `reduced_rhss`: ROMの右辺。
  * `linear_projection_eqs`: 線形投影マッピング $\mathbf y=V\hat{\mathbf y}$。
