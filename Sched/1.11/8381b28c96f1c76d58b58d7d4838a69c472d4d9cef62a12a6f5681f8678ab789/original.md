```
Scheduler(; timefunc=_time, delayfunc=sleep)
```

Initialize a new Scheduler instance, passing optionaly the time and delay functions

The scheduler struct defines a generic interface to scheduling events.  It needs two functions to actually deal with the “outside world”

  * The `timefunc` should be callable without arguments, and return a number (the “time”, in any units whatsoever). `timefunc` default is `UTCDateTimeFunc`.
  * The `delayfunc` function should be callable with one argument, compatible  with the output of `timefunc`, and should delay that many time units. delayfunc  will also be called with the argument 0 after each event is run to allow other threads an opportunity to run in multi-threaded applications.
