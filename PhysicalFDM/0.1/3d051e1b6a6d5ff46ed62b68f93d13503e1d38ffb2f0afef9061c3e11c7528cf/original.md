```julia
diff_mat(n; ...) -> Any
diff_mat(
    n,
    order;
    T,
    dt,
    points,
    lpoints,
    rpoints,
    fitting_order,
    boundary,
    boundary_points,
    boundary_order,
    sparse
) -> Any

```

Generate differential matrix.

# Arguments

  * `n`: Matrix size. If `v` is length `n` vector, diff_mat(n)*v calculate the differential of `v`.
  * `order`: Differential order.
  * `T`: Matrix element type. If set `T=Rational` or `using SymPy` and set `T=Sym`, `diff_mat` will return the exact value.
  * `dt`: Numerical differential step size.
  * `points`: Number of points for fitting polynomial to estimate differential. This argument is only for convenience. The real number of points is always `lpoints+rpoints+1`.
  * `lpoints`: Number of points at left to the target point, which differential is calculated by the fitted polynomial.
  * `rpoints`: Number of points at right to the target point. If `lpoints==rpoints`, then the differential is estimated as central finite difference. If `lpoints==0`, then it is normal forward finite difference. If `rpoints==0`, then it is backward finite difference.
  * `fitting_order`: The order of the fitted polynomial for estimating differential.
  * `boundary`: Boundary condition. Can be `Dirichlet()`(boundary value is zero), `Periodic()`(assume data is periodic), `:Extrapolation`(boundary value is extrapolated according to `boundary_points` and `boundary_order`), `:None`(not deal with boundary, will return non-square matrix).
  * `boundary_points`: Number of points for fitting polynomial to estimate differential at boundary. Normally it should not be much less than `points`, otherwise sometimes the current point may not be used to estimate the differential.
  * `boundary_order`: The order of the fitted polynomial for points determined by `boundary_points`.
  * `sparse`: If true, return sparse matrix instead of dense one.

Author: Qian, Long. 2021-09 (github: longqian95)

# Examples

```
k=5; x=rand(k);
diff_mat(k,1;points=3)*x #do 3 points 1st order central differential ((x[n+1]-x[n-1])/2).
diff_mat(k,2;points=3)*x #do 3 points 2nd order central differential (x[n+1]+x[n-1]-2x[n]).
diff_mat(k,1;points=2,lpoints=0)*x #do the normal 1st order forward differential (x[n+1]-x[n]).
diff_mat(k,1;lpoints=1,rpoints=0)*x #do the 1st order backward differential (x[n-1]-x[n]).
```
