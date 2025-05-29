```
Broyden <: AbstractQuasiNewtonUpdateRule
```

は[`AbstractQuasiNewtonDirectionUpdate`](@ref)において、リーマン的クワジ・ニュートン法でリーマン的ブロイデン更新が使用されることを示しており、これは[`BFGS`](@ref)と[`DFP`](@ref)の凸結合として表されます。

$$
\widetilde{H}_k^\mathrm{Br}
$$

をベクトル輸送とその逆を連結した演算子とし、$x_{k+1} = R_{x_k}(α_k η_k)$に作用させる前後に適用します。すると、更新式は次のようになります。

$$
H^\mathrm{Br}_{k+1} = \widetilde{H}^\mathrm{Br}_k
  - \frac{\widetilde{H}^\mathrm{Br}_k s_k s^{\mathrm{T}}_k \widetilde{H}^\mathrm{Br}_k}{s^{\mathrm{T}}_k \widetilde{H}^\mathrm{Br}_k s_k} + \frac{y_k y^{\mathrm{T}}_k}{s^{\mathrm{T}}_k y_k}
  + φ_k s^{\mathrm{T}}_k \widetilde{H}^\mathrm{Br}_k s_k
  \Bigl(
        \frac{y_k}{s^{\mathrm{T}}_k y_k} - \frac{\widetilde{H}^\mathrm{Br}_k s_k}{s^{\mathrm{T}}_k \widetilde{H}^\mathrm{Br}_k s_k}
  \Bigr)
  \Bigl(
        \frac{y_k}{s^{\mathrm{T}}_k y_k} - \frac{\widetilde{H}^\mathrm{Br}_k s_k}{s^{\mathrm{T}}_k \widetilde{H}^\mathrm{Br}_k s_k}
  \Bigr)^{\mathrm{T}}
$$

ここで、$s_k$と$y_k$は現在の基底に関する座標ベクトル（[`QuasiNewtonState`](@ref)から）であり、

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{および}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

それぞれ、$φ_k$はデフォルトで`:constant`のブロイデン因子ですが、`:Davidon`に設定することもできます。

# コンストラクタ

```
Broyden(φ, update_rule::Symbol = :constant)
```
