```
Currents(currents[, adjacency_matrix])
```

Creates a `Currents` instance for `currents`.

## Arguments

  * `currents`: The `AbstractCurrents` object to be turned into `Currents`. That might be time-consuming,   because  this requires evaluation of the current between all pairs.
  * `adjacency_matrix`: If provided, the current will be evaluated only between adjacent sites.

## Examples

```jldoctest
julia> using LatticeModels

julia> lat = SquareLattice(4, 4); site1, site2 = lat[1:2];

julia> H0 = tightbinding_hamiltonian(lat); psi = groundstate(H0);

julia> H1 = tightbinding_hamiltonian(lat, field=LandauGauge(0.1));

julia> currents = DensityCurrents(H1, psi)
Density currents for system:
One particle on 16-site SquareLattice in 2D space

julia> c2 = Currents(currents)
Currents{SparseArrays.SparseMatrixCSC{Float64, Int64}} on 16-site SquareLattice in 2D space

julia> c2[site1, site2] ≈ currents[site1, site2]
true
```
