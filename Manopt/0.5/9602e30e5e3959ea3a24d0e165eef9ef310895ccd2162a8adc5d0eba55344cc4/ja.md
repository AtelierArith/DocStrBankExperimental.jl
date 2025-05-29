```
SR1 <: AbstractQuasiNewtonUpdateRule
```

は、[`AbstractQuasiNewtonDirectionUpdate`](@ref) において、リーマン多様体のSR1更新がリーマン準ニュートン法で使用されることを示しています。

$$
\widetilde{H}_k^\mathrm{SR1}
$$

をベクトル輸送とその逆を前後に連結した演算子とし、$x_{k+1} = R_{x_k}(α_k η_k)$ に作用させます。すると、更新式は次のようになります。

$$
H^\mathrm{SR1}_{k+1} = \widetilde{H}^\mathrm{SR1}_k
+ \frac{
  (y_k - \widetilde{H}^\mathrm{SR1}_k s_k) (y_k - \widetilde{H}^\mathrm{SR1}_k s_k)^{\mathrm{T}}
}{
(y_k - \widetilde{H}^\mathrm{SR1}_k s_k)^{\mathrm{T}} s_k
}
$$

ここで、$s_k$ と $y_k$ は現在の基底に関する座標ベクトルであり（[`QuasiNewtonState`](@ref) から）、

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{および}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

それぞれを表します。

この方法は、分母が $r\lVert s_k\rVert_{x_{k+1}}\lVert y_k - \widetilde{H}^\mathrm{SR1}_k s_k \rVert_{x_{k+1}}$ より大きい場合にのみ更新を行うことで安定化できます（ここで $r>0$）。詳細については、[NocedalWright:2006](@cite) のセクション6.2を参照してください。

# コンストラクタ

```
SR1(r::Float64=-1.0)
```

`SR1` 更新を生成します。
