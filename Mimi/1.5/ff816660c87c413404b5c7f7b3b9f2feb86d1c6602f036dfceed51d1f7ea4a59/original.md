```
hasvalue(arr::TimestepArray, ts::VariableTimestep, idxs::Int...)
```

Return `true` or `false`, `true` if the TimestepArray `arr` contains the Timestep `ts` within indices `idxs`. Used when Array and Timestep have different TIMES, validating all dimensions.
