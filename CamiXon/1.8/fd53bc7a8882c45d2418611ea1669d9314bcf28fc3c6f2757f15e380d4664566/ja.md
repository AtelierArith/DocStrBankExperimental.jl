```
silvera_goldman_triplet(r::T) where T<:Real
```

パラメータ化された *Hartree* a.u. の三重項 $(^{3}\Sigma_{u}^{+})$ ポテンシャルは、電子の基底状態の $\mathrm{H}_{2}$ (Eh = 219474.6 cm-1) に対して、

$$
   V_{t}(r)=\mathrm{exp}\left(0.09678-1.10173\thinspace r-0.0394\thinspace r^{2}\right)+F(r)\left(-6.5\thinspace r^{-6}-124\thinspace r^{-8}-3285r^{-10}\thinspace \right)
$$

$$
   \mathrm{where}\ \ \ \ \ \ \ \  F(r) = \begin{cases}
\mathrm{exp}\left[-\left(\frac{10.04}{r}-1\right)^{2}\right] & \mathrm{for}\,\,\,r<10.04\,\mathrm{a.u.}\\
1 & \mathrm{for}\,\,\,r<10.04\,\mathrm{a.u.}
\end{cases}
$$

I.F. Silvera, - Rev. Mod. Phys., 52, 393 (1980) を参照してください。
