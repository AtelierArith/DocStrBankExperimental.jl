```
steadystate_fourier(
    H_0::QuantumObject,
    H_p::QuantumObject,
    H_m::QuantumObject,
    ωd::Number,
    c_ops::Union{Nothing,AbstractVector,Tuple} = nothing;
    n_max::Integer = 2,
    tol::R = 1e-8,
    solver::FSolver = SteadyStateLinearSolver(),
    kwargs...,
)
```

周期的に駆動されるシステムの定常状態を計算します。ここで `H_0` は駆動されていないシステムのハミルトニアンまたはリウビリアンです。周波数 $\omega_d$ の単色駆動を考慮し、これを `H_p` と `H_m` の2つの部分に分けます。`H_p` は $e^{i \omega t}$ として振動し、`H_m` は $e^{-i \omega t}$ として振動します。この関数には2つのソルバーが利用可能です：

  * `SteadyStateLinearSolver`: 線形方程式系を解きます。
  * `SSFloquetEffectiveLiouvillian`: 効率的なリウビリアンを解きます。

どちらの場合も、`n_max` は考慮するフーリエ成分の数であり、`tol` はソルバーの許容誤差です。

`SteadyStateLinearSolver` の場合、完全な線形系が一度に解かれます：

$$
( \mathcal{L}_0 - i n \omega_d ) \hat{\rho}_n + \mathcal{L}_1 \hat{\rho}_{n-1} + \mathcal{L}_{-1} \hat{\rho}_{n+1} = 0
$$

これは次の形の三重対角線形系です：

$$
\mathbf{A} \cdot \mathbf{b} = 0
$$

ここで

$$
\mathbf{A} = \begin{pmatrix}
\mathcal{L}_0 - i (-n_{\textrm{max}}) \omega_{\textrm{d}} & \mathcal{L}_{-1} & 0 & \cdots & 0 \\
\mathcal{L}_1 & \mathcal{L}_0 - i (-n_{\textrm{max}}+1) \omega_{\textrm{d}} & \mathcal{L}_{-1} & \cdots & 0 \\
0 & \mathcal{L}_1 & \mathcal{L}_0 - i (-n_{\textrm{max}}+2) \omega_{\textrm{d}} & \cdots & 0 \\
\vdots & \vdots & \vdots & \ddots & \vdots \\
0 & 0 & 0 & \cdots & \mathcal{L}_0 - i n_{\textrm{max}} \omega_{\textrm{d}}
\end{pmatrix}
$$

および

$$
\mathbf{b} = \begin{pmatrix}
\hat{\rho}_{-n_{\textrm{max}}} \\
\hat{\rho}_{-n_{\textrm{max}}+1} \\
\vdots \\
\hat{\rho}_{0} \\
\vdots \\
\hat{\rho}_{n_{\textrm{max}}-1} \\
\hat{\rho}_{n_{\textrm{max}}}
\end{pmatrix}
$$

これにより、すべての $\hat{\rho}_n$ を同時に取得できます。

`SSFloquetEffectiveLiouvillian` の場合、代わりに、行列連分数法を使用して効率的なリウビリアンが計算されます。

!!! note "異なる戻り値"
    2つのソルバーは異なるオブジェクトを返します。`SteadyStateLinearSolver` は、各フーリエ成分の密度行列を含む [`QuantumObject`](@ref) のリストを返します（$\hat{\rho}_{-n}$、$n$ は $0$ から $n_\textrm{max}$ まで）、一方 `SSFloquetEffectiveLiouvillian` は $\hat{\rho}_0$ のみを返します。


!!! note
    `steadystate_floquet` は `steadystate_fourier` の同義語です。


## 引数

  * `H_0::QuantumObject`: 駆動されていないシステムのハミルトニアンまたはリウビリアン。
  * `H_p::QuantumObject`: $e^{i \omega t}$ として振動する駆動の部分のハミルトニアンまたはリウビリアン。
  * `H_m::QuantumObject`: $e^{-i \omega t}$ として振動する駆動の部分のハミルトニアンまたはリウビリアン。
  * `ωd::Number`: 駆動の周波数。
  * `c_ops::Union{Nothing,AbstractVector} = nothing`: オプションの崩壊演算子。
  * `n_max::Integer = 2`: 考慮するフーリエ成分の数。
  * `tol::R = 1e-8`: ソルバーの許容誤差。
  * `solver::FSolver = SteadyStateLinearSolver`: 使用するソルバー。
  * `kwargs...`: ソルバーに渡される追加のキーワード引数。
