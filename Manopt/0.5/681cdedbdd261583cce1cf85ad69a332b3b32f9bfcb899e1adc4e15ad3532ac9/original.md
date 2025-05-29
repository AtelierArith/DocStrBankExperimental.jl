```
DebugTime()
```

Measure time and print the intervals. Using `start=true` you can start the timer on construction, for example to measure the runtime of an algorithm overall (adding)

The measured time is rounded using the given `time_accuracy` and printed after [canonicalization](https://docs.julialang.org/en/v1/stdlib/Dates/#Dates.canonicalize).

# Keyword parameters

  * `io=stdout`:             default stream to print the debug to.
  * `format="$prefix %s"`:   format to print the output, where `%s` is the canonicalized time`.
  * `mode=:cumulative`:      whether to display the total time or reset on every call using `:iterative`.
  * `prefix="Last Change:"`: prefix of the debug output (ignored if you set `format`:
  * `start=false`:           indicate whether to start the timer on creation or not.  Otherwise it might only be started on first call.
  * `time_accuracy=Millisecond(1)`: round the time to this period before printing the canonicalized time
