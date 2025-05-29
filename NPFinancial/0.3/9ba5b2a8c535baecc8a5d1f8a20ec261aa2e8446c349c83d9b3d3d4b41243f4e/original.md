```
rate(nper::Integer, pmt::Real, pv::Real, fv::Real, when=:end, guess=0.1, tol=1e-6, maxiter=100)
```

Compute interest rate given present value `pv`, future value `fv`, and fixed periodic payment `pmt` over a number of periods `nper`.

This implementation uses Newton's iteration until the change is less than 1e-6. Newton's rule is

$r_{n+1} = r_{n} - \frac{g(r_n)}{g'(r_n)}$

where

  * g(r) is the formula
  * g'(r) is the derivative with respect to r.

# Examples

```
julia> rate(1, 0, -100, 101)
0.010000000000000155
```
