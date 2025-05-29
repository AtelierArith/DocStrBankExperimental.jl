```
decreasing_v_terminator([quiet])
```

Construct termination criterion to stop integration when `v` is decreasing.

Note that some systems may truly have decreasing `v` as physical solutions — including eccentric systems and possibly precessing systems.  You may prefer to implement another solution, like detecting when `v` decreases below some threshold, or detecting when `v` is decreasing too quickly.  See this function's source code for a simple

If this terminator is triggered while `v` is less than 0.35, a warning will always be issued; otherwise an `info` message will be issued only if the `quiet` flag is set to `false`.
