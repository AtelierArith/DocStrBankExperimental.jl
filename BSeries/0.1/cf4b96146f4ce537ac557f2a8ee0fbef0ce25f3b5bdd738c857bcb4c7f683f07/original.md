```
bseries(csrk::ContinuousStageRungeKuttaMethod, order)
```

Compute the B-series of the [`ContinuousStageRungeKuttaMethod`](@ref) `csrk` up to the prescribed integer `order` as described by Miyatake & Butcher (2016).

!!! note "Normalization by elementary differentials"
    The coefficients of the B-series returned by this method need to be multiplied by a power of the time step divided by the `symmetry` of the rooted tree and multiplied by the corresponding elementary differential of the input vector field $f$. See also [`evaluate`](@ref).


# Examples

The [`AverageVectorFieldMethod`](@ref) is given by the parameter matrix with single entry one.

```jldoctest
julia> M = fill(1//1, 1, 1)
1×1 Matrix{Rational{Int64}}:
 1

julia> series = bseries(ContinuousStageRungeKuttaMethod(M), 4)
TruncatedBSeries{RootedTree{Int64, Vector{Int64}}, Rational{Int64}} with 9 entries:
  RootedTree{Int64}: Int64[]      => 1
  RootedTree{Int64}: [1]          => 1
  RootedTree{Int64}: [1, 2]       => 1//2
  RootedTree{Int64}: [1, 2, 3]    => 1//4
  RootedTree{Int64}: [1, 2, 2]    => 1//3
  RootedTree{Int64}: [1, 2, 3, 4] => 1//8
  RootedTree{Int64}: [1, 2, 3, 3] => 1//6
  RootedTree{Int64}: [1, 2, 3, 2] => 1//6
  RootedTree{Int64}: [1, 2, 2, 2] => 1//4

julia> series - bseries(AverageVectorFieldMethod(), order(series))
TruncatedBSeries{RootedTree{Int64, Vector{Int64}}, Rational{Int64}} with 9 entries:
  RootedTree{Int64}: Int64[]      => 0
  RootedTree{Int64}: [1]          => 0
  RootedTree{Int64}: [1, 2]       => 0
  RootedTree{Int64}: [1, 2, 3]    => 0
  RootedTree{Int64}: [1, 2, 2]    => 0
  RootedTree{Int64}: [1, 2, 3, 4] => 0
  RootedTree{Int64}: [1, 2, 3, 3] => 0
  RootedTree{Int64}: [1, 2, 3, 2] => 0
  RootedTree{Int64}: [1, 2, 2, 2] => 0
```

# References

  * Yuto Miyatake and John C. Butcher. "A characterization of energy-preserving methods and the construction of parallel integrators for Hamiltonian systems." SIAM Journal on Numerical Analysis 54, no. 3 (2016): [DOI: 10.1137/15M1020861](https://doi.org/10.1137/15M1020861)
