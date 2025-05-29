```
easingflat(t, b, c, d)
```

A flat easing function, same as `lineartween()`.

For all easing functions, the four parameters are:

  * `t` time, ie the current framenumber
  * `b` beginning position or bottom value of the range
  * `c` total change in position or top value of the range
  * `d` duration, ie a framecount

1. `t/d` or `t/=d` normalizes `t` to between 0 and 1
2. `... * c` scales up to the required range value
3. `... + b` adds the initial offset
