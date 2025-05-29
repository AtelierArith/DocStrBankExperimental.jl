```
interval(a, b)
```

`interval(a, b)` checks whether [a, b] is a valid `Interval`, using the (non-exported) `is_valid_interval` function. If so, then an `Interval(a, b)` object is returned; if not, a warning is printed and the empty interval is returned.
