```
CyclicPeriods{S<:NothingPeriod}
```

Contains information for calculating the cyclic constraints. The parameter `S` should be either an `AbstractStrategicPeriod` or `AbstractRepresentativePeriod`.

# Fields

  * **`last_per::S`** is the last period in the case of `S<:AbstractRepresentativePeriod` or the current period in the case of `S<:AbstractStrategicPeriod` as the last strategic period is not relevant.
  * **`current_per::S`** is the current period in both the case of `S<:AbstractRepresentativePeriod` and `S<:AbstractStrategicPeriod`.
