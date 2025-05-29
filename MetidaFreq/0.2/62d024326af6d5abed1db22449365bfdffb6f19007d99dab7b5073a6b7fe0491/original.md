```
diffci(x1, n1, x2, n2; level = 0.95, method = :default)
```

Proportion difference (x1 / n1 - x2 / n2) confidence interval.

  * 'method'
  * `:mn` | `:default`- Miettinen & Nurminen;  Miettinen, O. and Nurminen, M. (1985), Comparative analysis of two rates. Statist. Med., 4: 213-226. doi:10.1002/sim.4780040211;
  * `:fm` | `:mee` - Mee maximum likelihood method; Mee RW (1984) Confidence bounds for the difference between two probabilities,Biometrics40:1175-1176
  * `:wald` - Wald CI without CC;
  * `:waldcc` - Wald CI with CC;
  * `:nhs`  - Newcombes Hybrid (wilson) Score interval; Newcombe RG (1998), Interval Estimation for the Difference Between Independent Proportions: Comparison of Eleven Methods. Statistics in Medicine 17, 873-890;
  * `:nhscc` - Newcombes Hybrid Score CC; Newcombe (1998);
  * `:ac` -  Agresti-Caffo interval; Agresti A, Caffo B., “Simple and effective confidence intervals for proportions and differences of proportions result from adding two successes and two failures”, American Statistician 54: 280–288 (2000);
  * `:ha` - Hauck-Andersen; Hauck, W. W., & Anderson, S. (1986). A Comparison of Large-Sample Confidence Interval Methods for the Difference of Two Binomial Probabilities. The American Statistician, 40(4), 318–322. doi:10.1080/00031305.1986.10475426 ;
  * `:mover` - Method of variance estimates recovery;
  * `:jeffrey` - Brown, Li's Jeffreys.

# Reference:

  * Brown, L.D., Cai, T.T., and DasGupta, A. Interval estimation for a binomial proportion. Statistical Science, 16(2):101–117, 2001.
  * Farrington, C. P. and Manning, G. (1990), “Test Statistics and Sample Size Formulae for Comparative Binomial Trials with Null Hypothesis of Non-zero Risk Difference or Non-unity Relative Risk,” Statistics in Medicine, 9, 1447–1454
  * Li HQ, Tang ML, Wong WK. Confidence intervals for ratio of two Poisson rates using the methodof variance estimates recovery. Computational Statistics 2014; 29(3-4):869-889
  * Brown, L., Cai, T., & DasGupta, A. (2003). INTERVAL ESTIMATION IN EXPONENTIAL FAMILIES. Statistica Sinica, 13(1), 19-49.
