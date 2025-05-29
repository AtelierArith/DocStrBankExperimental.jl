```
modelsteppredict(data::RheoTimeData, model::RheoModel; step_on::Real = 0.0)
```

Same as `modelpredict` but assumes a step loading with step starting at `step_on` or closest actual value to that specified. If the loading data is variable, the magnitude in the middle of the array is used.
