```
BetaRegressionModel{T,L1,L2,V,M} <: RegressionModel
```

Type representing a regression model for beta-distributed response values in the open interval (0, 1), as described by Ferrari and Cribari-Neto (2004).

The mean response is linked to the linear predictor by a link function with type `L1 <: Link01`, i.e. the link must map $(0, 1) \mapsto \mathbb{R}$ and use the GLM package's interface for link functions. While there is no canonical link function for the beta regression model as there is for GLMs, logit is the most common choice.

The precision is transformed by a link function with type `L2 <: Link` which should map $\mathbb{R} \mapsto \mathbb{R}$ or, ideally, $(0, \infty) \mapsto \mathbb{R}$ because the precision must be positive. The most common choices are the identity, log, and square root links.
