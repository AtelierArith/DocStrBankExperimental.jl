```
struct ADOs
```

The Auxiliary Density Operators for HEOM model.

# Fields

  * `data` : the vectorized auxiliary density operators
  * `dimensions` : the dimension list of the coupling operator (should be equal to the system dimensions).
  * `N` : the number of auxiliary density operators
  * `parity`: the parity label (`EVEN` or `ODD`).

!!! note "`dims` property"
    For a given `ados::ADOs`, `ados.dims` or `getproperty(ados, :dims)` returns its `dimensions` in the type of integer-vector.


# Methods

One can obtain the density matrix for specific index (`idx`) by calling : `ados[idx]`. `HierarchicalEOM.jl` also supports the following calls (methods) :

```julia
length(ados);  # returns the total number of `ADOs`
ados[1:idx];   # returns a vector which contains the `ADO` (in matrix form) from index `1` to `idx`
ados[1:end];   # returns a vector which contains all the `ADO` (in matrix form)
ados[:];       # returns a vector which contains all the `ADO` (in matrix form)
for rho in ados  # iteration
    # do something
end
```
