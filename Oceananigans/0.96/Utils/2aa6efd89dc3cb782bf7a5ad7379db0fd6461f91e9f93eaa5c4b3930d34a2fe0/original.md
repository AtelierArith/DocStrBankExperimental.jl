```
IterationInterval(interval; offset=0)
```

Return a callable `IterationInterval` that "actuates" (schedules output or callback execution) whenever the model iteration (modified by `offset`) is a multiple of `interval`.

For example,

  * `IterationInterval(100)` actuates at iterations `[100, 200, 300, ...]`.
  * `IterationInterval(100, offset=-1)` actuates at iterations `[99, 199, 299, ...]`.
