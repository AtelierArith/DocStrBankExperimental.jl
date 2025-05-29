```
rangeclamp(f, hi=20, lo=-hi; replacement=NaN)
```

Modify `f` so that values of `f(x)` outside of `[lo,hi]` are replaced by `replacement`.

Examples

```
f(x) = 1/x
plot(rangeclamp(f), -1, 1)
plot(rangeclamp(f, 10), -1, 1) # no `abs(y)` values exceeding 10
```
