```
quick_cancel(d)
```

Cancel out matching factors from numerator and denominator. This is not as effective as `simplify_fractions`, for example, it wouldn't simplify `(x^2 + 15 -  8x)  / (x - 5)` to `(x - 3)`. But it will simplify `(x - 5)^2*(x - 3) / (x - 5)` to `(x - 5)*(x - 3)`. Has optimized processes for `Mul` and `Pow` terms.
