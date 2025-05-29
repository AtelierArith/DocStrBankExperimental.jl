```
AshbaughHatch(; cutoff, use_neighbors, shortcut, ϵ_mixing, σ_mixing,
              λ_mixing, weight_special)
```

Ashbaugh-Hatchポテンシャル（$V_{\text{AH}}$）は、2つの原子間の修正されたLennard-Jones（$V_{\text{LJ}}$）6-12相互作用です。

ポテンシャルエネルギーは次のように定義されます。

$$
V_{\text{LJ}}(r_{ij}) = 4\varepsilon_{ij} \left[\left(\frac{\sigma_{ij}}{r_{ij}}\right)^{12} - \left(\frac{\sigma_{ij}}{r_{ij}}\right)^{6}\right] \\ 
$$

$$
V_{\text{AH}}(r_{ij}) =
    \begin{cases}
      V_{\text{LJ}}(r_{ij}) +\varepsilon_{ij}(1-λ_{ij}) &,  r_{ij}\leq  2^{1/6}σ  \\
       λ_{ij}V_{\text{LJ}}(r_{ij})  &,  2^{1/6}σ \leq r_{ij}
    \end{cases}
$$

および各原子に対する力は次のように表されます。

$$
\vec{F}_{\text{AH}} =
    \begin{cases}
      F_{\text{LJ}}(r_{ij})  &,  r_{ij} \leq  2^{1/6}σ  \\
       λ_{ij}F_{\text{LJ}}(r_{ij})  &,  2^{1/6}σ \leq r_{ij}
    \end{cases}
$$

ここで

$$
\begin{aligned}
\vec{F}_{\text{LJ}}\
&= \frac{24\varepsilon_{ij}}{r_{ij}^2} \left[2\left(\frac{\sigma_{ij}^{6}}{r_{ij}^{6}}\right)^2 -\left(\frac{\sigma_{ij}}{r_{ij}}\right)^{6}\right]  \vec{r_{ij}}
\end{aligned}
$$

もし$\lambda$が1であれば、これは標準の[`LennardJones`](@ref)ポテンシャルを与えます。
