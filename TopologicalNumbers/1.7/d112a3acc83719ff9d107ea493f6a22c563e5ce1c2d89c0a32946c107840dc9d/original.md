```
Z2Problem{T1<:Function,T2<:Union{Int,Nothing},T3<:Union{Tuple,AbstractVector,Int},T4<:Bool} <: TopologicalNumbersProblems
```

A struct representing a problem for calculating the Z2 number.

# Fields

  * `H::T1`: The Hamiltonian function `H=H(k, p)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector and `p` contains parameter. Dimension of `k` must be 2.
  * `Nfill::T2`: The number of filled bands. `nothing` means the half-filling. Default is `nothing`.
  * `N::T3`: The number of points for one direction in the Brillouin zone. Default is 50.
  * `rounds::T4`: A boolean indicating whether to round a returned variable. Default is true.
  * `TR::T4`: A boolean indicating whether to calculate the remaining part of the Brillouin zone. If `true`, `solve` returns an additional result `TRTopologicalNumber`. If the calculation is done nomally, `TRTopologicalNumber` is equal to `TopologicalNumber`. Default is false.

# Example

```julia
julia> 
```
