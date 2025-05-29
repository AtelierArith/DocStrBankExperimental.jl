```
InvGaussianCopula{P}
```

Fields:

  * θ::Real - parameter

Constructor

```
InvGaussianCopula(θ)
```

The bivariate Inverse Gaussian copula is parameterized by $\theta \in [0,\infty)$. It is an Archimedean copula with generator :

$$
\phi(t) = \exp{\frac{1-\sqrt{1+2θ^{2}t}}{θ}}.
$$

More details about Inverse Gaussian Archimedean copula are found in :

```
Mai, Jan-Frederik, and Matthias Scherer. Simulating copulas: stochastic models, sampling algorithms, and applications. Vol. 6. # N/A, 2017. Page 74.
```

It has a few special cases:

  * When θ = 0, it is the IndependentCopula

References:

  * [nelsen2006](@cite) Nelsen, Roger B. An introduction to copulas. Springer, 2006.
