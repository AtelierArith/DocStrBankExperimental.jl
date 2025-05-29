```
EmpiricalVariogram(partition, var₁, var₂=var₁; [options])
```

Compute the empirical (cross-)variogram of the geospatial `partition` for variables `var₁` and `var₂` as described in Hoffimann & Zadrozny 2019.

Forwards `options` to the underlying [`EmpiricalVariogram`](@ref) calls with geospatial data.

## References

  * Hoffimann, J and Zadrozny, B. 2019. [Efficient variography with partition variograms](https://www.sciencedirect.com/science/article/pii/S0098300419302936)
