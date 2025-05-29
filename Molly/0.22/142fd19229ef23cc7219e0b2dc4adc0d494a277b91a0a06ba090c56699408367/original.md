```
virial(sys, neighbors=find_neighbors(sys), step_n=0; n_threads=Threads.nthreads())
virial(inter, sys, neighbors, step_n; n_threads=Threads.nthreads())
```

Calculate the virial of a system or the virial resulting from a general interaction.

The virial is defined as

$$
\Xi = -\frac{1}{2} \sum_{i,j>i} r_{ij} \cdot F_{ij}
$$

Custom general interaction types can implement this function.

This should only be used on systems containing just pairwise interactions, or where the specific interactions, constraints and general interactions without [`virial`](@ref) defined do not contribute to the virial.
