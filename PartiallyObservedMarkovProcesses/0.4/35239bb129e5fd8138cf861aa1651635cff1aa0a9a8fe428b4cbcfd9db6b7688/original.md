```
euler(stepfun; dt)
```

The function `stepfun` should advance the state by an arbitrary time-increment. The time-increment will be chosen so that equal-sized steps of duration at most `dt` are taken over any desired interval.
