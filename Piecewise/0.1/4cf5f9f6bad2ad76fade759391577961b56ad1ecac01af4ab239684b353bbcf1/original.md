```
moment(f::PiecewiseFunction, n::Integer)
```

Moment of order `n` of the piecewise function `f`:

$$
(M\circ f)(n) = \int_{-\infty}^{\infty}dx\,f(x)x^n
$$
