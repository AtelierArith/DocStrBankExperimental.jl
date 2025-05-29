```
InverseSR1 <: AbstractQuasiNewtonUpdateRule
```

は、[`AbstractQuasiNewtonDirectionUpdate`](@ref) において、逆リーマン SR1 更新がリーマン準ニュートン法で使用されることを示しています。

$$
\widetilde{B}_k^\mathrm{SR1}
$$

をベクトル輸送とその逆を前後に連結した演算子とし、$x_{k+1} = R_{x_k}(α_k η_k)$ に作用させます。すると、更新式は次のようになります。

$$
B^\mathrm{SR1}_{k+1} = \widetilde{B}^\mathrm{SR1}_k
+ \frac{
  (s_k - \widetilde{B}^\mathrm{SR1}_k y_k) (s_k - \widetilde{B}^\mathrm{SR1}_k y_k)^{\mathrm{T}}
}{
  (s_k - \widetilde{B}^\mathrm{SR1}_k y_k)^{\mathrm{T}} y_k
}
$$

ここで、$s_k$ と $y_k$ は現在の基底に関する座標ベクトルであり（[`QuasiNewtonState`](@ref) から）、

$$
T^{S}_{x_k, α_k η_k}(α_k η_k) \quad\text{および}\quad
\operatorname{grad}f(x_{k+1}) - T^{S}_{x_k, α_k η_k}(\operatorname{grad}f(x_k)) ∈ T_{x_{k+1}} \mathcal{M},
$$

それぞれを表します。

この方法は、分母が $r\lVert y_k\rVert_{x_{k+1}}\lVert s_k - \widetilde{H}^\mathrm{SR1}_k y_k \rVert_{x_{k+1}}$ より大きい場合にのみ更新を行うことで安定化できます（ここで $r>0$）。詳細については、[NocedalWright:2006](@cite) のセクション 6.2 を参照してください。

# コンストラクタ

```
InverseSR1(r::Float64=-1.0)
```

`InverseSR1` を生成します。
