```
InverseDFP <: AbstractQuasiNewtonUpdateRule
```

は、[`AbstractQuasiNewtonDirectionUpdate`](@ref) において、逆リーマン DFP 更新がリーマン準ニュートン法で使用されることを示しています。

$$
\widetilde{B}_k^\mathrm{DFP}
$$

をベクトル輸送とその逆を前後に連結した演算子とし、$x_{k+1} = R_{x_k}(α_k η_k)$ に作用させます。すると、更新式は次のようになります。

$$
B^\mathrm{DFP}_{k+1} = \widetilde{B}^\mathrm{DFP}_k + \frac{s_k s^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
  - \frac{\widetilde{B}^\mathrm{DFP}_k y_k y^{\mathrm{T}}_k \widetilde{B}^\mathrm{DFP}_k}{y^{\mathrm{T}}_k \widetilde{B}^\mathrm{DFP}_k y_k}
$$

ここで、$s_k$ と $y_k$ は、現在の基底（[`QuasiNewtonState`](@ref) から）に関する座標ベクトルであり、

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{および}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

それぞれを表します。
