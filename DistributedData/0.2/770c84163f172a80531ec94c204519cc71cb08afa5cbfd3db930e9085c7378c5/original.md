```
dtransform(val, fn, workers, tgt::Symbol=val)
```

Transform the worker-local distributed data available as `val` on `workers` in-place, by a function `fn`. Store the result as `tgt` (default `val`)

# Example

```
# multiply all saved data by 2
dtransform(:myData, (d)->(2*d), workers())
```
