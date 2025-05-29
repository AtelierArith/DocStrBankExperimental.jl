```
@event f(farg...) c(carg...)
@event f(farg...) ca
```

Schedule a function `f(farg...)` as a conditional event to a clock.

# Arguments

  * `f`: function to be executed at event time,
  * `farg...`: its arguments, the first argument must be a clock,
  * `c`: function to be evaluated at the clock's sample rate, if it   returns true, the event is triggered,
  * `carg...`: arguments to c,
  * `ca`: an anyonymous function of the form `()->...` to be evaluated    at the clock's sample rate, if it returns true, the event   is triggered.
