```
CycleLife <: AbstractBatteryLife
```

A life type corresponding to a linear degradation of the battery lifetime up to a given number of cycles.

## Fields

  * **`cycles::Int`** is the number of cycles that the battery can tolerate.
  * **`degradation::Float64`** is the relative allowed capacity reduction at the end of life of the battery.
  * **`stack_cost::TimeProfile`** is the relative cost for replacing a battery stack once it reached its maximum number of cycles.
