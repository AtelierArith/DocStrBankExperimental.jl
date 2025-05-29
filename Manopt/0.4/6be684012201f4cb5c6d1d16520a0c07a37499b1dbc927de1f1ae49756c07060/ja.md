```
DFP <: AbstractQuasiNewtonUpdateRule
```

は、リーマン準ニュートン法でリーマン DFP 更新が使用されることを示しています。

$$
\widetilde{H}_k^\mathrm{DFP}
$$

をベクトル輸送とその逆を前後に連結した演算子とし、$x_{k+1} = R_{x_k}(α_k η_k)$ に作用させます。すると、更新式は次のようになります。

$$
H^\mathrm{DFP}_{k+1} = \Bigl(
  \mathrm{id}_{T_{x_{k+1}} \mathcal{M}} - \frac{y_k s^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
\Bigr)
\widetilde{H}^\mathrm{DFP}_k
\Bigl(
  \mathrm{id}_{T_{x_{k+1}} \mathcal{M}} - \frac{s_k y^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
\Bigr) + \frac{y_k y^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
$$

ここで、$s_k$ と $y_k$ は、現在の基底に関する座標ベクトル（[`QuasiNewtonState`](@ref) から）であり、

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{および}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

それぞれを表します。
