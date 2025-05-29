```
JarqueBeraTestPooled(ud::UncertainDataset, n::Int = 1000) -> JarqueBeraTest
```

First, draw `n` realisations of each uncertain value in `ud` and pool them together. Then, compute the Jarque-Bera statistic to test the null hypothesis that the values of the pool are normally distributed.
