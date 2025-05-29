```
printsstate([io::IO,] ssd::SteadyStateData)
```

Display steady state solution.

Steady state solution is presented in a table, where the first column is the name of the variable, the second and third columns are the corresponding values of the level and the slope. If the value is not determined (as per its `mask` value) then it is displayed as "*".
