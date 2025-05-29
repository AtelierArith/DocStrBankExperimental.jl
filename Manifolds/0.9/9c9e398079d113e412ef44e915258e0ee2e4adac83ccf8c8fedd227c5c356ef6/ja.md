```
project(G::SpecialLinear, p)
```

プロジェクト $p ∈ \mathrm{GL}(n, 𝔽)$ を [`SpecialLinear`](@ref) 群 $G=\mathrm{SL}(n, 𝔽)$ に。

$$
p
$$

の特異値分解を $p = U S V^\mathrm{H}$ と書くと、射影の公式は次のようになります。

$$
\operatorname{proj}_{\mathrm{SL}(n, 𝔽)}(p) = U S D V^\mathrm{H},
$$

ここで

$$
D_{ij} = δ_{ij} \begin{cases}
    1            & \text{ if } i ≠ n \\
    \det(p)^{-1} & \text{ if } i = n
\end{cases}.
$$
