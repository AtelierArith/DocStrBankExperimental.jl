```
project(G::SpecialLinear, p, X)
```

点対称に $X ∈ 𝔽^{n×n}$ を $p$ の接空間に射影します。[`SpecialLinear`](@ref) $G = \mathrm{SL}(n, 𝔽)$ のための公式は次のようになります。

$$
\operatorname{proj}_{p}
    = (\mathrm{d}L_p)_e ∘ \operatorname{proj}_{𝔰𝔩(n, 𝔽)} ∘ (\mathrm{d}L_p^{-1})_p
    \colon X ↦ X - \frac{\operatorname{tr}(X)}{n} I,
$$

ここで、最後の表現は接空間の表現をリー代数として使用しています。
