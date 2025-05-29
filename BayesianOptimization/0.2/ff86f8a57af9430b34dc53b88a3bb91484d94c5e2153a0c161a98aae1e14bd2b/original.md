Scales `βt` of `UpperConfidenceBound` as

```
βt = √(2 * log(t^(D/2 + 2) * π^2/(3δ)))
```

where `t` is the number of observations, `D` is the dimensionality of the input data points and δ is a small constant (default δ = 0.1).

See Brochu E., Cora V. M., de Freitas N. (2010), "A Tutorial on Bayesian Optimization of Expensive Cost Functions, with Application to Active User Modeling and Hierarchical Reinforcement Learning", https://arxiv.org/abs/1012.2599v1 page 16.
