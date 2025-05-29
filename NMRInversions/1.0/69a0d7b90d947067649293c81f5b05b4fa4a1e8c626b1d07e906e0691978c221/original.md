```
pdhgm(σ, τ)
```

Primal dual hybrid gradient method for L1 regularization,  following [this paper](https://doi.org/10.1016/j.jmr.2017.05.010) [Reci2017](@cite) It can be used as a "solver" for the invert function.

The particular choice of σ and τ is heuristic.  A smaller σ will increase the stability while reducing the convergence speed of the algorithm. A good compromise between the two was found when σ = 0.1 and τ = 10.  The best values of σ and τ will depend slightly on the scaling of the signal.  Therefore, it is best to normalize the NMR signal to a maximum of 1, a technique which was followed in the cited study.

Note that for this method, the role of α is inverted, with larger α values leading to less smoothing, not more. For that reason, `alpha=gcv()` (Mitchell method) will not work. Please use `alpha=gcv(starting_value)` or `alpha=gcv(lower*limit, upper*limit)', or some lcurve method instead.
