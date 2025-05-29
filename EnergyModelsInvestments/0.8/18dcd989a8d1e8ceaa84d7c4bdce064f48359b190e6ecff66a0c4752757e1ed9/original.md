```
PeriodLife <: LifetimeMode
```

The investment is considered to last only for the investment period. The excess lifetime is considered in the rest value. If the lifetime is lower than the length of the period, reinvestment is considered as well.

# Fields

  * **`lifetime::TimeProfile`** is the chosen lifetime of the technology.
