This module provides `tick()`, `tock()`, and `tok()` functions.

  * `tick()`        start a new timer and start counting
  * `tock()`        stop counting, show total elapsed time in canonical form
  * `tok()`         stop counting, show and return total elapsed time in seconds
  * `peektimer()    continue counting, show and return elapsed seconds so far
  * `peektimers()   continue counting, show and return elapsed seconds so far
  * `laptimer()     continue counting, show elapsed time so far in canonical form
  * `alarm(h, m, s) set an alarm in h/m/s from now
  * `alarm(dt)      set an alarm for the date and time`dt`
  * `alarmlist()    list alarms

Don't use these for timing code execution! Julia provides much better facilities for measuring performance, ranging from the `@time` and `@elapsed` macros to packages such as [BenchmarkTools.jl](https://github.com/JuliaCI/BenchmarkTools.jl).
