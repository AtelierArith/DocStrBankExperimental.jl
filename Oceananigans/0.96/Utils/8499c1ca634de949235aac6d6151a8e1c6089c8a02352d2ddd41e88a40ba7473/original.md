```
prettytime(t, longform=true)
```

Convert a floating point value `t` representing an amount of time in SI units of seconds to a human-friendly string with three decimal places. Depending on the value of `t` the string will be formatted to show `t` in nanoseconds (ns), microseconds (μs), milliseconds (ms), seconds, minutes, hours, or days.

With `longform=false`, we use s, m, hrs, and d in place of seconds, minutes, and hours.
