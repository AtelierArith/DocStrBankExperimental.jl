```
pulse(delta::TimePeriod[; epoch::DateTime])
```

Obtain a node which ticks every `delta`. Each value will equal the time of the knot.

Knots will be placed such that the difference between its time and `epoch` will always be an integer multiple of `delta`. By default `epoch` is set to the Julia `DateTime` epoch, which is `DateTime(0, 12, 31)`.
