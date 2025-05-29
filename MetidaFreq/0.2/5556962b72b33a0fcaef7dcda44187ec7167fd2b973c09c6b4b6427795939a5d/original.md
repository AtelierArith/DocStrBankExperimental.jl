```
orci(x1, n1, x2, n2; level = 0.95, method = :default)
```

Odd ratio confidence interval.

  * `:mn` - MN Score (Miettinen&Nurminen, 1985);
  * `:fm` | `:mee` - FM (same as MN Score, but not multiplied on `(n1 + n2) * (n1 + n2 - 1)`) (Mee RW, 1984; Farrington&Manning, 1990);
  * `:woolf` - Woolf logit (Woolf, 1955);
  * `:awoolf` - Adjusted Woolf interval (Gart adjusted logit) (Gart, 1966; Lawson, 2005);
  * `:mover` - Method of variance estimates recovery (MOVER) (Donner&Zou, 2012);

Reference:

  * Miettinen O. S., Nurminen M. (1985) Comparative analysis of two rates.Statistics in Medicine 4,213–226;
  * Mee RW (1984) Confidence bounds for the difference between two probabilities,Biometrics 40:1175-1176;
  * Farrington, C. P. and Manning, G. (1990), “Test Statistics and Sample Size Formulae for Comparative Binomial Trials with Null Hypothesis of Non-zero Risk Difference or Non-unity Relative Risk,” Statistics in Medicine, 9, 1447–1454;
  * Woolf, B. (1955). On estimating the relation between blood group and disease. Annals of human genetics, 19(4):251-253;
  * Gart, J. J. (1966). Alternative analyses of contingency tables. Journal of the Royal Statistical Society. Series B (Methodological), 28:164-179;
  * Lawson, R (2005). Smallsample confidence intervals for the odds ratio.  Communication in Statistics Simulation and Computation, 33, 1095-1113;
  * Donner, A. and Zou, G. (2012). Closed-form confidence intervals for functions of the normal mean and standard deviation. Statistical Methods in Medical Research, 21(4):347-359.
