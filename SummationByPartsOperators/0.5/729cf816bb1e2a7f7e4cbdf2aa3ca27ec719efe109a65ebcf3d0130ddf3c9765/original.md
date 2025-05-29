```
periodic_derivative_operator(source::Holoborodko2008,
                             derivative_order, accuracy_order,
                             xmin, xmax, N; mode=FastMode(), kwargs...)
periodic_derivative_operator(source::Holoborodko2008;
                             derivative_order, accuracy_order,
                             xmin, xmax, N, mode=FastMode(), kwargs...)
```

Create a `PeriodicDerivativeOperator` approximating the `derivative_order`-th derivative on a uniform grid between `xmin` and `xmax` with `N` grid points up to order of accuracy `accuracy_order` where the leftmost grid point used is determined by `left_offset`. The evaluation of the derivative can be parallelized using threads by choosing `mode=ThreadedMode()`.

## Examples

```jldoctest
julia> periodic_derivative_operator(Holoborodko2008(), derivative_order=1, accuracy_order=2,
                                    xmin=0.0, xmax=1.0, N=11)
Periodic first-derivative operator of order 2 on a grid in [0.0, 1.0] using 11 nodes,
stencils with 2 nodes to the left, 2 nodes to the right, and coefficients of   Holoborodko (2008)
  Smooth Noise Robust Differentiators.
  http://www.holoborodko.com/pavel/numerical-methods/numerical-derivative/smooth-low-noise-differentiators/
```
