```
periodic_derivative_operator(source::LanczosLowNoise;
                             derivative_order = 1,
                             accuracy_order,
                             stencil_width = accuracy_order + 3,
                             xmin, xmax, N,
                             mode = FastMode())
```

Create a `PeriodicDerivativeOperator` approximating the `derivative_order`-th derivative on a uniform grid between `xmin` and `xmax` with `N` grid points up to order of accuracy `accuracy_order` where `stencil_width` determines the number of nodes used for the finite difference stencil. The evaluation of the derivative can be parallelized using threads by choosing `mode = ThreadedMode()`.

## Examples

```jldoctest
julia> D = periodic_derivative_operator(LanczosLowNoise();
                                        accuracy_order = 2,
                                        xmin = 0.0, xmax = 1.0, N = 10)
Periodic first-derivative operator of order 2 on a grid in [0.0, 1.0] using 10 nodes,
stencils with 2 nodes to the left, 2 nodes to the right, and coefficients of   Holoborodko (2008)
  Smooth Noise Robust Differentiators.
  http://www.holoborodko.com/pavel/numerical-methods/numerical-derivative/lanczos-low-Noise-differentiators/

julia> Matrix(D)
10×10 Matrix{Float64}:
  0.0   1.0   2.0   0.0   0.0   0.0   0.0   0.0  -2.0  -1.0
 -1.0   0.0   1.0   2.0   0.0   0.0   0.0   0.0   0.0  -2.0
 -2.0  -1.0   0.0   1.0   2.0   0.0   0.0   0.0   0.0   0.0
  0.0  -2.0  -1.0   0.0   1.0   2.0   0.0   0.0   0.0   0.0
  0.0   0.0  -2.0  -1.0   0.0   1.0   2.0   0.0   0.0   0.0
  0.0   0.0   0.0  -2.0  -1.0   0.0   1.0   2.0   0.0   0.0
  0.0   0.0   0.0   0.0  -2.0  -1.0   0.0   1.0   2.0   0.0
  0.0   0.0   0.0   0.0   0.0  -2.0  -1.0   0.0   1.0   2.0
  2.0   0.0   0.0   0.0   0.0   0.0  -2.0  -1.0   0.0   1.0
  1.0   2.0   0.0   0.0   0.0   0.0   0.0  -2.0  -1.0   0.0

julia> D = periodic_derivative_operator(LanczosLowNoise();
                                        accuracy_order = 2,
                                        xmin = 0 // 1, xmax = 1 // 1, N = 10,
                                        stencil_width = 7)
Periodic first-derivative operator of order 2 on a grid in [0//1, 1//1] using 10 nodes,
stencils with 3 nodes to the left, 3 nodes to the right, and coefficients of   Holoborodko (2008)
  Smooth Noise Robust Differentiators.
  http://www.holoborodko.com/pavel/numerical-methods/numerical-derivative/lanczos-low-Noise-differentiators/
```
