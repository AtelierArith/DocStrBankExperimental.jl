# 拡張ヘルプ

```
σ(d::AbstractVector, E::Ellipsoid)
```

### アルゴリズム

$$
E
$$

を中心$c$と形状行列$Q = BB^\mathrm{T}$を持つ楕円体とします。方向$d$に沿ったその支持ベクトルは、単位ユークリッド球$\mathcal{B}_2$の支持ベクトルから代数的関係を用いて導出できます。

$$
σ_{B\mathcal{B}_2 ⊕ c}(d) = c + Bσ_{\mathcal{B}_2} (B^\mathrm{T} d)
= c + \dfrac{Qd}{\sqrt{d^\mathrm{T}Q d}}.
$$
