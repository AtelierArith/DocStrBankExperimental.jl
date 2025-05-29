```
moment(f::PiecewiseFunction, n::Integer)
```

区分関数 `f` の順序 `n` のモーメント：

$$
(M\circ f)(n) = \int_{-\infty}^{\infty}dx\,f(x)x^n
$$
