```
pressure(sys, neighbors=find_neighbors(sys), step_n=0; n_threads=Threads.nthreads())
```

Calculate the pressure of a system.

The pressure is defined as

$$
P = \frac{1}{V} \left( NkT - \frac{2}{D} \Xi \right)
$$

where `V` is the system volume, `N` is the number of atoms, `k` is the Boltzmann constant, `T` is the system temperature, `D` is the number of dimensions and `Ξ` is the virial calculated using [`virial`](@ref).

This should only be used on systems containing just pairwise interactions, or where the specific interactions, constraints and general interactions without [`virial`](@ref) defined do not contribute to the virial. Not compatible with infinite boundaries.
