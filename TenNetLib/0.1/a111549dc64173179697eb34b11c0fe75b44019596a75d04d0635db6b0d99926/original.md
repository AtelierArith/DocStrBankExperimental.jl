```
function Float64_threshold()
function Float64_threshold(threshold::Float)
```

Returns threshold for floating point calculations. In most places, any number below this will be treated zero. E.g., in `cutoff`. Default: `1e-15`.

Optionally, change the threshold as per the input `threshold`.
