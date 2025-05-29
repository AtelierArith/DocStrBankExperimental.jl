`BasisSet(basis1, basis2, ...)`

$$
\{ \phi_1, \phi_2, \phi_3, \cdots  \}
$$

基底セットは、Rayleigh-Ritz法の入力です。次のように基底セットを定義できます：

$$
\begin{aligned}
  \phi_1(r) &= \exp(-13.00773 ~r^2), \\
  \phi_2(r) &= \exp(-1.962079 ~r^2), \\
  \phi_3(r) &= \exp(-0.444529 ~r^2), \\
  \phi_4(r) &= \exp(-0.1219492 ~r^2).
\end{aligned}
$$

```@example
BS = BasisSet(
  SimpleGaussianBasis(13.00773),
  SimpleGaussianBasis(1.962079),
  SimpleGaussianBasis(0.444529),
  SimpleGaussianBasis(0.1219492),
)
```
