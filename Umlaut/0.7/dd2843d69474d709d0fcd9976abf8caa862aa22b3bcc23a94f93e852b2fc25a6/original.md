```
mkcall(fn, args...; val=missing, kwargs=(;))
```

Convenient constructor for Call operation. If val is `UncalculatedValue` (default) and call value can be calculated from (bound) variables and constants, they are calculated. To prevent this behavior, set val to some neutral value.
