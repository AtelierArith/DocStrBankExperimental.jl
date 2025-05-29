```
throttle(f::Function, args...; maxfps = 0.03)
```

Create a throttled `Signal` whos action `f(args...)` will be called only if `1/maxfps` time has passed since the last time it updated. The resulting `Signal` will be updated maximum of `maxfps` times per second.
