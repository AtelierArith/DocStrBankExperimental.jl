```
DissipationLaxFriedrichsEntropyVariables(max_abs_speed=max_abs_speed_naive)
```

エントロピー安定性が証明されたローカルなLax-Friedrichs型の散逸オペレーターを作成します。このオペレーターは、エントロピー保存型の二点フラックス関数（例：`flux_ec`）と一緒に使用され、エントロピー安定な表面フラックスを生成します。表面フラックス関数は次のように初期化できます：

```julia
flux_es = FluxPlusDissipation(flux_ec, DissipationLaxFriedrichsEntropyVariables())
```

特に、数値フラックスは次の形を持ちます

$$
f^{\mathrm{ES}} = f^{\mathrm{EC}} - \frac{1}{2} \lambda_{\mathrm{max}} H (w_r - w_l),
$$

ここで、$f^{\mathrm{EC}}$はエントロピー保存型の二点フラックス関数（例：`flux_ec`で計算される）、$\lambda_{\mathrm{max}}$は`max_abs_speed(u_l, u_r, orientation_or_normal_direction, equations)`として推定される最大波速度で、デフォルトは[`max_abs_speed_naive`](@ref)、$H$は左状態`u_l`と右状態`u_r`に依存する対称正定値散逸行列であり、$(w_r - w_l)$はエントロピー変数のジャンプです。理想的には、$H (w_r - w_l) = (u_r - u_l)$となり、散逸オペレーターはローカルLax-Friedrichs散逸と整合性があります。

エントロピー安定な散逸オペレーターは、関数`function (dissipation::DissipationLaxFriedrichsEntropyVariables)(u_l, u_r, orientation_or_normal_direction, equations)`を使用して計算され、各方程式に特化する必要があります。

多イオンGLM-MHD方程式の散逸行列の導出については、次を参照してください：

  * A. Rueda-Ramírez, A. Sikstel, G. Gassner, An Entropy-Stable Discontinuous Galerkin Discretization of the Ideal Multi-Ion Magnetohydrodynamics System (2024). Journal of Computational Physics. [DOI: 10.1016/j.jcp.2024.113655](https://doi.org/10.1016/j.jcp.2024.113655).

```
