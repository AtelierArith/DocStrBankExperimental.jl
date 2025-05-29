```
w, Xi = get_measure(M, t::Int64 = 2*M[:degree]-1 ,lambda = [(-1)^(k-1) for k in 1:M[:nu]])
```

Return the approximation of the moment sequence $\sum_{i=1}^{\nu} \lambda_i \mu_i$ truncated to moments of degree <= t (default: twice the order of the relaxation minus 2), as weighted sum of Dirac measures: $\sum_{k=1}^{r} \omega_k \delta_{\xi_k}$ where

  * `w` is the vector of weights of the Dirac measures.
  * `Xi` is matrix of $n\times r$ support points of the corresponding Dirac measures. The column `Xi[:,i]` is the support point $\xi_{i}$ of the ith Dirac measure and its weights is `w[i]`.

```julia
w, Xi = get_measure(M)

([0.1541368146508854, 0.5889741915171074, 0.256888993597116], [1.4142135624216647 1.414213562080608 1.4142135620270329; -1.732052464639053 1.4141771454788292 1.7319839273833693])
```
