```
AbstractDiffEqArray{T, N, A} <: AbstractVectorOfArray{T, N, A}
```

An AbstractVectorOfArray object which has extra information of a time array `A.t` in order to specify a time series. A canonical AbstractDiffEqArray is for example the pairing `DiffEqArray([[1,2],[3,4]],[1.0,2.0])` which means that at time 1.0 the values were `[1,2]` and at time 2.0 the values were `[3,4]`.

An AbstractDiffEqArray has all of the same behaviors as an AbstractVectorOfArray with the additional properties:

## Fields

An AbstractDiffEqArray adds the following fields:

  * `t` which holds the times of each timestep.
