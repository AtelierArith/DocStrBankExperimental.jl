```
periodic_derivative_operator(derivative_order, accuracy_order,
                             xmin, xmax, N,
                             left_offset=-(accuracy_order+1)÷2,
                             mode=FastMode())
periodic_derivative_operator(; derivative_order, accuracy_order,
                             xmin, xmax, N,
                             left_offset=-(accuracy_order+1)÷2,
                             mode=FastMode())
```

Create a [`PeriodicDerivativeOperator`](@ref) approximating the `derivative_order`-th derivative on a uniform grid between `xmin` and `xmax` with `N` grid points up to order of accuracy `accuracy_order` where the leftmost grid point used is determined by `left_offset`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode())`.

## Examples

```jldoctest
julia> periodic_derivative_operator(derivative_order=1, accuracy_order=2,
                                    xmin=0.0, xmax=1.0, N=11)
Periodic first-derivative operator of order 2 on a grid in [0.0, 1.0] using 11 nodes,
stencils with 1 nodes to the left, 1 nodes to the right, and coefficients of Fornberg (1998)
  Calculation of Weights in Finite Difference Formulas.
  SIAM Rev. 40.3, pp. 685-691.
```
