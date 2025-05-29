```
manifold_dimension(M::SymmetricPositiveSemidefiniteFixedRank)
```

[`SymmetricPositiveSemidefiniteFixedRank`](@ref) 行列 `M` の次元を数体系 `𝔽` に対して返します。すなわち、

$$
\begin{aligned}
\dim \operatorname{SPS}_{k,ℝ}(n) &= kn - \frac{k(k-1)}{2},\\
\dim \operatorname{SPS}_{k,ℂ}(n) &= 2kn - k^2,
\end{aligned}
$$

ここで、最後の $k^2$ はエルミート行列の対角におけるゼロの虚部によるものです。
