```
x, w = custom_gauss_rule(lo, hi, a, b, endpt, maxits=maxiterations[T])
```

Generates the points `x` and weights `w` for a Gauss rule with weight function `w(x)` on the interval `lo < x < hi`.

The arrays `a` and `b` hold the coefficients (as given, for instance, by `legendre_coeff`) in the three-term recurrence relation for the monic orthogonal polynomials `p(0,x)`, `p(1,x)`, `p(2,x)`, ... , that is,

```
p(k, x) = (x-a[k]) p(k-1, x) - b[k]² p(k-2, x),    k ≥ 1,
```

where `p(0, x) = 1` and, by convention, `p(-1, x) = 0` with

```
          hi
b[1]^2 = ∫  w(x) dx.
         lo
```

Thus, `p(k, x) = xᵏ + lower degree terms` and

```
 hi
∫  p(j, x) p(k, x) w(x) dx = 0 if j ≠ k.
lo
```
