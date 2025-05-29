```
subsecond(ep::Epoch, n)
```

Get the number of fractional seconds with the unit $s * \frac{1}{10^n}$, e.g. `subsecond(ep, 3)` for milliseconds, of the epoch `ep`. `n` must be divisible by 3.
