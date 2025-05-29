```
MSEp(R::AbstractDataset{D,T}, R_test, p; method, ntype, stepsize) -> error
```

Compute mean squared error of iterated predictions of length `p` using test set `R_test`.

## Description

This error measure takes in a prediction model consisting of `R`, `method`, `ntype` and `stepsize` and evaluates its performance. The test set `R_test` is a delay reconstruction with the same delay `τ` and dimension `D` as `R`. For each subset of `R_test` with length `p` it calls `localmodel_tsp`. The model error is then defined as

$$
\begin{aligned}
MSE_p = \frac{1}{p|T_{ref}|}\sum_{t\in T_{ref}}\sum_{i=1}^{p} \left(y_{t+i}
- y_{pred,t+i} \right)^2
\end{aligned}
$$

where $|T_{ref}|$ is the number of subsets of `R_test` used.

## References

See [`localmodel_tsp`](@ref).
