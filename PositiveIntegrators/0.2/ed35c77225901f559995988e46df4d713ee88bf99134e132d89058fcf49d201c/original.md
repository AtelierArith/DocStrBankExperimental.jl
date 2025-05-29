```
prob_pds_minmapk
```

Positive and nonconservative autonomous nonlinear PDS

$$
\begin{aligned}
u_1' &= k_6u_6-k_7u_1-k_1u_1u_2 +k_2u_4,\\
u_2' &= k_5u_3-k_1u_2u_2,\\
u_3' &= k_2u_4-k_3u_1u_3+k_4u_5-k_5u_3,\\
u_4' &= k_1u_1u_2-k_2u_4,\\
u_5' &= k_3u_1u_3-k_4u_5,\\
u_6' &= k_7u_1-k_6u_6,
\end{aligned}
$$

with constants

$$
\begin{aligned}
k_1 &=\frac{100}{3}, & k_2 &=\frac{1}{3}, & k_3 &=50,\\
k_4 &=0.5, & k_5 &=\frac{10}{3} ,  & k_6 &= 0.1,\\
k_7 &= 0.1.
\end{aligned}
$$

The initial value is $\mathbf{u}_0 = (0.1, 0.175, 0.15, 1.15, 0.81, 0.5)^T$ and the time domain $(0, 200)$. There are two independent linear invariants, e.g. $u_1+u_4+u_6=1.75$ and $u_2+u_3+u_4+u_5 =2.285$.

## References

  * Sergio Blanes, Arieh Iserles, and Shev Macnamara. "Positivity preserving methods for ordinary differential equations." ESAIM: Mathematical Modelling and Numerical Analysis 56 (2022): 1843–1870. [DOI: 10.1051/m2an/2022042](https://doi.org/10.1051/m2an/2022042)
  * Otto Hadač, František Muzika, Vladislav Nevoral, Michal Přibyl, and Igor Schreiber "Minimal oscillating subnetwork in the Huang-Ferrell model of the MAPK cascade." PLoS ONE 12 (2017): e0178457. [DOI: 10.1371/journal.pone.0178457](https://doi.org/10.1371/journal.pone.0178457)
