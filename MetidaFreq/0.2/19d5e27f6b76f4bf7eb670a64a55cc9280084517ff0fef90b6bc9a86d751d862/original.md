```
rrci(x1, n1, x2, n2; level = 0.95, method = :default)
```

Risk ratio confidence interval.

  * `:mn` - Miettinen-Nurminen Score interval (Miettinen&Nurminen, 1985);
  * `:fm` | `:mee` - FM Score interval (Mee RW, 1984; Farrington&Manning, 1990);
  * `:cli` - Crude log interval, Gart (Gart&Nam, 1988);
  * `:li` | `:wald` - Log interval / Katz / Wald interval (Katz et al, 1978);
  * `:mover` - Method of variance estimates recovery (Donner&Zou, 2012);

Reference:

  * Miettinen, O. and Nurminen, M. (1985), Comparative analysis of two rates. Statist. Med., 4: 213-226. doi:10.1002/sim.4780040211;
  * Mee RW (1984) Confidence bounds for the difference between two probabilities,Biometrics 40:1175-1176;
  * Farrington, C. P., & Manning, G. (1990). Test statistics and sample size formulae for comparative binomial trials with null hypothesis of non-zero risk difference or non-unity relative risk. Statistics in Medicine, 9(12), 1447–1454. doi:10.1002/sim.4780091208;
  * Gart, JJ and Nam, J (1988): Approximate interval estimation of the ratio of binomial parameters: Areview and corrections for skewness. Biometrics 44, 323-338;
  * Katz D, Baptista J, Azen SP and Pike MC. Obtaining confidence intervals for the risk ratio in cohort studies. Biometrics 1978; 34: 469–474;
  * Donner, A. and Zou, G. (2012). Closed-form confidence intervals for functions of the normal mean and standard deviation. Statistical Methods in Medical Research, 21(4):347-359.
