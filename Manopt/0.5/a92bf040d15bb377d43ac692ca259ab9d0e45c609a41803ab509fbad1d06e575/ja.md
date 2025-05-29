```
InverseBroyden <: AbstractQuasiNewtonUpdateRule
```

[`AbstractQuasiNewtonDirectionUpdate`](@ref) で、リーマン・ブロイデン更新がリーマン・準ニュートン法で使用されることを示しており、これは [`InverseBFGS`](@ref) と [`InverseDFP`](@ref) の凸結合として表されます。

$$
\widetilde{H}_k^\mathrm{Br}
$$

をベクトル輸送とその逆を連結した演算子とし、$x_{k+1} = R_{x_k}(α_k η_k)$ に作用させます。すると、更新式は次のようになります。

$$
B^\mathrm{Br}_{k+1} = \widetilde{B}^\mathrm{Br}_k
 - \frac{\widetilde{B}^\mathrm{Br}_k y_k y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k}{y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k y_k}
   + \frac{s_k s^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
 + φ_k y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k y_k
 \Bigl(
     \frac{s_k}{s^{\mathrm{T}}_k y_k} - \frac{\widetilde{B}^\mathrm{Br}_k y_k}{y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k y_k}
    \Bigr) \Bigl(
        \frac{s_k}{s^{\mathrm{T}}_k y_k} - \frac{\widetilde{B}^\mathrm{Br}_k y_k}{y^{\mathrm{T}}_k \widetilde{B}^\mathrm{Br}_k y_k}
 \Bigr)^{\mathrm{T}}
$$

ここで、$s_k$ と $y_k$ は現在の基底に関する座標ベクトルであり（[`QuasiNewtonState`](@ref) から）、

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{および}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

それぞれ、$φ_k$ はブロイデン因子であり、デフォルトでは `:constant` ですが、`：Davidon` に設定することもできます。

# コンストラクタ

```
InverseBroyden(φ, update_rule::Symbol = :constant)
```
