```
GPUNeighborFinder(; eligible, dist_cutoff, special, n_steps_reorder, initialized)
```

Use the non-bonded forces/potential energy algorithm from [Eastman and Pande 2010](https://doi.org/10.1002/jcc.21413) to avoid calculating a neighbor list.

This is the recommended neighbor finder on NVIDIA GPUs.
