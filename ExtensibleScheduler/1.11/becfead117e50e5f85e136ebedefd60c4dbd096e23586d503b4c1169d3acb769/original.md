```
BlockingScheduler(; clock=real_time_clock, delayfunc=_sleep, jobconfig=JobConfig())
```

`BlockingScheduler` is the simplest scheduler. It implements `AbstractScheduler`.

This is a monothread implementation of scheduling job.

# Optional arguments

  * `clock::AbstractClock`: clock that will be used by scheduler (it's by default `real_time_clock`, which is system UTC time but a `SimClock` struct can also be passed for simulation purpose).
  * `delayfunc::DelayFunc`: functor which is responsible (when called) of waiting until next task should be fired (`_sleep` is used by default but a `NoSleep` struct can also be passed for simulation purpose).
  * `jobconfig::JobConfig`: job configuration default settings (`misfire_grace_period`...)
