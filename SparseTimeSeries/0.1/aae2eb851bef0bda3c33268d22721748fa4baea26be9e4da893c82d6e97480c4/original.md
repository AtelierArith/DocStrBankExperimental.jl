`EventSeries` holds a vector of `values` toghether with its corresponding `timestamps`. `EventSeries` is subtype `AbstractVector`, and of both `timestamps` and `values` must be subtypes of `AbstractVector`.

EventSeries(timestamps::U, values::W, ::TrustInput)

```
- Assumes that `timestamps` and `values` are of equal
  length, and that `timestamps` is sorted.
```

EventSeries(timestamps, values; drop*repeated=true, keep*end=true)

```
- Checks that `timestamps` and `values` are of equal length
- Checks that `timestamps` is sorted
- Throws `AssertionError` if any of the above mentioned checks failss.
- If `drop_repeated` is true (default) all repeated values in values,
  and corresponding timestamps, are removed before construction.
- If `keep_end` is true (default), the last value in values (with its
  corresponding timestamp) is kept regardless of whether it equals the
  previous value. Keep_end will only be considered if `drop_repeated`
  is true.
```
