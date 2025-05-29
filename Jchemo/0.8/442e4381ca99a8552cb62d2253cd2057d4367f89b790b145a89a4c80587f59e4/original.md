```
savgk(nhwindow::Int, degree::Int, deriv::Int)
```

Compute the kernel of the Savitzky-Golay filter.

  * `nhwindow` : Nb. points (>= 1) of the half window.
  * `degree` : Degree of the smoothing polynom, where  1 <= `degree` <= 2 * nhwindow.
  * `deriv` : Derivation order, where 0 <= `deriv` <= degree.

The size of the kernel is odd (npoint = 2 * nhwindow + 1): 

  * x[-nhwindow], x[-nhwindow+1], ..., x[0], ...., x[nhwindow-1], x[nhwindow].

If `deriv` = 0, there is no derivation (only polynomial smoothing).

The case `degree` = 0 (i.e. simple moving average) is not  allowed by the funtion.

## References

Luo, J., Ying, K., Bai, J., 2005. Savitzky–Golay smoothing and differentiation  filter for even number data. Signal Processing 85, 1429–1434. https://doi.org/10.1016/j.sigpro.2005.02.002

## Examples

```julia
using Jchemo
res = savgk(21, 3, 2)
@names res
res.S 
res.G 
res.kern
```
