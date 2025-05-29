```
as_sentinel(x, v)
```

Reinterprets a Number Array or a Number `x` so that values in x that equal v will be treated as missing. This is done by reinterpreting the array as a `SentinelMissing` without copying the data.
