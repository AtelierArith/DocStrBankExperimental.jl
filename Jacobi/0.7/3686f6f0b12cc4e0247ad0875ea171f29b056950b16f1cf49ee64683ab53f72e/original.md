```
jacobi(x, n [, a [, b]])
djacobi(x, n [, a [, b]])
```

Computes Jacobi polynomial and derivatives of Jacobi polynomials.

This function computes the jacobi polynomial of degree `n` with weights `a` and `b` at point x ($P_n^{a,b}(x)$). There are several variants of the function with default values:

  * `jacobi(x, n)` (`a` and `b` are both zero)
  * `jacobi(x, n, a)` (`b` is zero)

The derivative of Jacobi polynomials ($\frac{dP_n^{a,b}(x)}{dx}$)are computed with functions that add a `d` in front of its name:

  * `djacobi`

Parameters:

  * `x` Where to calculate the polynomial
  * `n` Order of polynomial
  * `a` Weight α of the Jacobi polynomial
  * `b` Weight β of the Jacobi polynomial
  * returns: the value of the polynomial

### Examples

```julia
julia> x = 0.3; a = 0.2; b = 0.1; m = 5;

julia> y = jacobi(x, m, a, b)
0.3780304524166406

julia> dy = djacobi(x, m, a, b)
-0.4343764194492186
```
