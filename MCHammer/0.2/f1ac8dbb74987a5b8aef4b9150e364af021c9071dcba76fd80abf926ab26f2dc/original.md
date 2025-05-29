Generate a learning curve as a DataFrame for a given method. 

```
lc_curve(method::LearningCurveMethod, InitialEffort, TotalUnits, Learning; LotSize=1)
```

The DataFrame columns are:

  * `Units`: Production unit number.
  * `CurvePoint`: Cumulative cost/effort at that unit.
  * `IncrementalCost`: Difference in cumulative cost from the previous step.
  * `AvgCost`: Average cost per unit up to that point.
  * `Method`: A string identifier for the method.
