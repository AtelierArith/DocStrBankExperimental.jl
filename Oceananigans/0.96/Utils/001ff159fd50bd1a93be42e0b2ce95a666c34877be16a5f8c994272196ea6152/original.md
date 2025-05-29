```
WallTimeInterval(interval; start_time = time_ns() * 1e-9)
```

Return a callable `WallTimeInterval` that schedules periodic output or diagnostic evaluation on a `interval` of "wall time" while a simulation runs, in units of seconds.

The "wall time" is the actual real world time in seconds, as kept by an actual or hypothetical clock hanging on your wall.

The keyword argument `start_time` can be used to specify a starting wall time other than the moment `WallTimeInterval` is constructed.
