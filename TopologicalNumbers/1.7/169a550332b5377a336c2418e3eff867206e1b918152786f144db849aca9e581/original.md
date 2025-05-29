```
SCProblem{T1<:Function,T2<:Union{Int,Nothing},T3<:Union{Tuple,AbstractVector,Int},T4<:Bool} <: TopologicalNumbersProblems
```

A struct representing a problem for calculating the second Chern number.

# Fields

  * `H::T1`: The Hamiltonian function `H=H(k, p)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector and `p` contains parameter. Dimension of `k` must be 4.
  * `Nfill::T2`: The number of filled bands. `nothing` means the half-filling. Default is `nothing`.
  * `N::T3`: The number of points in the Brillouin zone. Type of `Int` means the uniform mesh. You can also specify the mesh by giving a tuple or a vector. Default is 30.
  * `RV::T4`: A boolean indicating whether to return a `real` value. Default is true.

# Example

```julia
julia> 
```
