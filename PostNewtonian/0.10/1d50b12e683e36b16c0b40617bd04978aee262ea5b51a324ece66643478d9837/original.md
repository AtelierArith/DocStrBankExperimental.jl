```
dtmin_terminator(T, [quiet])
```

Construct termination criterion to terminate when `dt` drops below `√eps(T)`.

Pass `force_dtmin=true` to `solve` when using this callback.  Otherwise, the time-step size may decrease too much *within* a single time step, so that the integrator itself will quit before reaching this callback, leading to a less graceful exit.

If this terminator is triggered while `v` is less than 0.35, a warning will always be issued; otherwise an `info` message will be issued only if the `quiet` flag is set to `false`.
