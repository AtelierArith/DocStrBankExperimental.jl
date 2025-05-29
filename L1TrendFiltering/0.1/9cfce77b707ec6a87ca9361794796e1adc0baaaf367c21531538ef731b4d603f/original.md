```
l1tf(y, λ; α = 1e-2, β = 5e-1, μ = 2, MAXITER = 40, MAXLSITER = 20, atol = 1e-4, verbose = false)

Find the solution of the L1 trend filtering problem using interior-point method:
minimize ``{\frac{1}{2}} \left\| y - x \right\|_{2}^{2} + \lambda \left\| D x \right\|_{1}``
where ``D`` is the second difference matrix.

The implmentation is based on original MATLAB code by authors.

### Optional Arguments
- `α = 1e-2`: backtracking linesearch parameter (0,0.5]
- `β = 5e-1`: backtracking linesearch parameter (0,1)
- `μ = 2`: IPM parameter: t update
- `MAXITER = 40`: IPM parameter: max iteration of IPM
- `MAXLSITER = 20`: IPM parameter: max iteration of line search
- `atol = 1e-4`: IPM parameter: tolerance

### References
- "l1 Trend Filtering", S. Kim, K. Koh, ,S. Boyd and D. Gorinevsky https://web.stanford.edu/~gorin/papers/l1_trend_filter.pdf#page=13.55
- https://web.stanford.edu/~boyd/l1_tf/
```
