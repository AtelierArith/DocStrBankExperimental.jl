```
simulate_signal(sequence, partitioned_parameters::AbstractVector{<:SimulationParameters})
```

In situations where the number of voxels is too large to store the intermediate `magnetization` array, the signal can be calculated in batches: the voxels are divided (by the user) into partitions and the signal is calculated for each partition separately. The final signal is the sum of the signals from all partitions.
