```
takens_best_estimate_dim(X, εmax, metric = Chebyshev(), εmin = 0)
```

「タケンズの最良推定」[^Takens1985][^Theiler1988]法を使用して、相関次元を推定します。

元の式は

$$
\Delta_C \approx \frac{C(\epsilon_\text{max})}{\int_0^{\epsilon_\text{max}}(C(\epsilon) / \epsilon) \, d\epsilon}
$$

ここで、$C$は[`correlationsum`](@ref)であり、$\epsilon_\text{max}$は上限カットオフです。ここでは後者の式を使用します。

$$
\Delta_C \approx - \frac{1}{\eta},\quad \eta = \frac{1}{(N-1)^*}\sum_{[i, j]^*}\log(||X_i - X_j|| / \epsilon_\text{max})
$$

ここで、合計はすべての$i, j$に対して行われ、$i < j$かつ$||X_i - X_j|| < \epsilon_\text{max}$となります。上記の式では、元の論文のバイアスはすでに修正されています。[ ^Borovkova1999]で提案されているように。

[^Borovkova1999]によれば、下限カットオフ`εmin`を導入することでアルゴリズムがより安定（発散しない）になる可能性があります。このオプションは提供されていますが、デフォルトはゼロです。

`X`が時系列`x`の遅延座標埋め込みから来る場合、$\epsilon_\text{max}$の推奨値は`std(x)/4`です。

次のように使用することもできます。

```julia
Δ_C, Δu_C, Δl_C = FractalDimensions.takens_best_estimate(args...)
```

上限および下限の95％信頼区間を取得します。区間は、関数が最大値から2だけ減少したときの`Δ_C`の値を見つけることによって、対数尤度関数から推定されます。例えば、[ ^Barlow]の第5.3章を参照してください。

[^Takens1985]: Takens, On the numerical determination of the dimension of an attractor, in: B.H.W. Braaksma, B.L.J.F. Takens (Eds.), Dynamical Systems and Bifurcations, in: Lecture Notes in Mathematics, Springer, Berlin, 1985, pp. 99–106.

[^Theiler1988]: Theiler, [Lacunarity in a best estimator of fractal dimension. Physics Letters A, 133(4–5)](https://doi.org/10.1016/0375-9601(88)91016-X)

[^Borovkova1999]: Borovkova et al., [Consistency of the Takens estimator for the correlation dimension. The Annals of Applied Probability, 9, 05 1999.](https://doi.org/10.1214/aoap/1029962747)

[^Barlow]: Barlow, R., Statistics - A Guide to the Use of Statistical Methods in the Physical Sciences. Vol 29. John Wiley & Sons, 1993
