```
is_energy_preserving(series_integrator)::Bool
```

This function checks whether the B-series `series_integrator` of a time integration method is energy-preserving for Hamiltonian systems - up to the [`order`](@ref) of `series_integrator`.

# References

This code is based on the Theorem 2 of

  * Elena Celledoni, Robert I. McLachlan, Brynjulf Owren, and G. R. W. Quispel. "Energy-preserving integrators and the structure of B-series." Foundations of Computational Mathematics 10 (2010): 673-693. [DOI: 10.1007/s10208-010-9073-1](https://link.springer.com/article/10.1007/s10208-010-9073-1)
