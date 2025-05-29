```
interval(a, b)
```

`interval(a, b)` checks whether [a, b] is a valid `Interval`, which is the case if `-∞ <= a <= b <= ∞`, using the (non-exported) `is_valid_interval` function. If so, then an `Interval(a, b)` object is returned; if not, then an error is thrown.
