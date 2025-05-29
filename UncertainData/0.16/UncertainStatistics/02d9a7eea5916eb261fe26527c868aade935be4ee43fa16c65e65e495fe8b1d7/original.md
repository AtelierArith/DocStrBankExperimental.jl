```
OneSampleADTestElementWise(ud::UncertainDataset,
    n::Int = 1000) -> Vector{JarqueBeraTest}
```

First, draw `n` realisations of each uncertain value in `ud`, keeping one pool of values for each uncertain value.

Then, compute the Jarque-Bera statistic to test the null hypothesis that each value pool is normally distributed.
