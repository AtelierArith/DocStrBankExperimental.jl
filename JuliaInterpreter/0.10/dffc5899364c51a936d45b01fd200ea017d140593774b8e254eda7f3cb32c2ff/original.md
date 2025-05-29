```
break_on(states...)
```

Turn on automatic breakpoints when any of the conditions described in `states` occurs. The supported states are:

  * `:error`: trigger a breakpoint any time an uncaught exception is thrown
  * `:throw` : trigger a breakpoint any time a throw is executed (even if it will eventually be caught)
