```
mid(a::Interval)
```

Find the midpoint of interval `a`.

For intervals of the form `[-∞, x]` or `[x, +∞]` where `x` is finite, return respectively `nextfloat(-∞)` and `prevfloat(+∞)`. Note that it differs from the behavior of `mid(a, α=0.5)`.
