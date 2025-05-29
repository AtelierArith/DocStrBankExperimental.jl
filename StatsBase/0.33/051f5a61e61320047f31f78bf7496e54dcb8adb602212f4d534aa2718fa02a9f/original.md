```
ConvergenceException(iters::Int, lastchange::Real=NaN, tol::Real=NaN)
```

The fitting procedure failed to converge in `iters` number of iterations, i.e. the `lastchange` between the cost of the final and penultimate iteration was greater than specified tolerance `tol`.
