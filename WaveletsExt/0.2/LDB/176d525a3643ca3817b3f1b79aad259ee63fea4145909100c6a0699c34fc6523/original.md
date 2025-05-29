```
AsymmetricRelativeEntropy <: ProbabilityDensityDM
```

Asymmetric Relative Entropy discriminant measure for the Probability Density and Time Frequency based energy maps. This measure is also known as cross entropy and Kullback-Leibler divergence.

Equation: 

$D(p,q) = \sum p(x) \log \frac{p(x)}{q(x)}$ 

where $\int_{-\infty}^{\infty} p(t) dt = \int_{-\infty}^{\infty} q(t) dt = 1$ ($p(t)$ and $q(t)$ are probability density functions.)
