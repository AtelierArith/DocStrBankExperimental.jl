```
KullbackLeibler(p::Function,q::Function,Domain::HyperCube=HyperCube([-15,15]); tol=2e-15, N::Int=Int(3e7), Carlo::Bool=(length(Domain)!=1))
```

Computes the Kullback-Leibler divergence between two probability distributions `p` and `q` over the `Domain`. If `Carlo=true`, this is done using a Monte Carlo Simulation with `N` samples. If the `Domain` is one-dimensional, the calculation is performed without Monte Carlo to a tolerance of ≈ `tol`.

$$
D_{\text{KL}}[p,q] \coloneqq \int \mathrm{d}^m y \, p(y) \, \mathrm{ln} \bigg( \frac{p(y)}{q(y)} \bigg)
$$
