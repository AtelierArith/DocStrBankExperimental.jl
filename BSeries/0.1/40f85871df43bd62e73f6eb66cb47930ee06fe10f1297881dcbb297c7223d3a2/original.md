```
ContinuousStageRungeKuttaMethod(M)
```

A struct that describes a continuous stage Runge-Kutta (CSRK) method. It can be constructed by passing the parameter matrix `M` as described by Miyatake and Butcher (2016). You can compute the B-series of the method by [`bseries`](@ref).

# References

  * Yuto Miyatake and John C. Butcher. "A characterization of energy-preserving methods and the construction of parallel integrators for Hamiltonian systems." SIAM Journal on Numerical Analysis 54, no. 3 (2016): [DOI: 10.1137/15M1020861](https://doi.org/10.1137/15M1020861)
