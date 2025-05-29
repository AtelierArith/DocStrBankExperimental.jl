```
gelmandiag(samples::AbstractArray{<:Real,3}; alpha::Real=0.95)
```

`samples`の形状が`(draws, chains, parameters)`であるGelman、Rubin、Brooks診断を計算します[^Gelman1992] [^Brooks1998]。診断の潜在的スケール縮小因子（PSRF）の値が1に近い場合、収束を示唆します。一般的な指針として、PSRFの97.5パーセンタイルが1.2を超える場合、収束は拒否されます。

[^Gelman1992]: Gelman, A., & Rubin, D. B. (1992). Inference from iterative simulation using multiple sequences. Statistical science, 7(4), 457-472.

[^Brooks1998]: Brooks, S. P., & Gelman, A. (1998). General methods for monitoring convergence of iterative simulations. Journal of computational and graphical statistics, 7(4), 434-455.
