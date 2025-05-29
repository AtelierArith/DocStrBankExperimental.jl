```
optimize(F, f, bounds_ul, bounds_ll, method = BCA(); logger = (status) -> nothing)
```

Approximate an optimal solution for the bilevel optimization problem `x ∈ argmin F(x, y)` with `x ∈ bounds_ul` subject to `y ∈ argmin{f(x,y) : y ∈ bounds_ll}`.

## Parameters

  * `F` upper-level objective function.
  * `f` lower-level objective function.
  * `bounds_ul, bounds_ll` upper and lower level boundaries (2×n matrices), respectively.
  * `logger` is a functions called at the end of each iteration.

## Example

```jldoctest
julia> F(x, y) = sum(x.^2) + sum(y.^2)
F (generic function with 1 method)

julia> f(x, y) = sum((x - y).^2) + y[1]^2
f (generic function with 1 method)

julia> bounds_ul = bounds_ll = [-ones(5)'; ones(5)']
2×5 Matrix{Float64}:
 -1.0  -1.0  -1.0  -1.0  -1.0
  1.0   1.0   1.0   1.0   1.0

julia> res = optimize(F, f, bounds_ul, bounds_ll)
+=========== RESULT ==========+
  iteration: 108
    minimum: 
          F: 7.68483e-08
          f: 3.96871e-09
  minimizer: 
          x: [1.0283390421119262e-5, -0.00017833559080058394, -1.612275010196171e-5, 0.00012064585960330227, 4.38964383738248e-5]
          y: [1.154609166391327e-5, -0.0001300400306798623, 1.1811981430188257e-6, 8.868498295184257e-5, 5.732849695863675e-5]
    F calls: 2503
    f calls: 5044647
    Message: Stopped due UL function evaluations limitations. 
 total time: 21.4550 s
+============================+
```
