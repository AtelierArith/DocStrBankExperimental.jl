```
struct BPProblem{T1<:Function,T2<:Union{Tuple,AbstractVector,Int},T3<:Real,T4<:Bool} <: TopologicalNumbersProblems
```

The `BPProblem` struct represents a problem for calculating Berry phase.

# Fields

  * `H::T1`: The Hamiltonian function `H=H(k, p)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector and `p` contains parameter. Dimension of `k` must be 1.
  * `N::T2`: The number of points for one direction in the Brillouin zone. Default is 51.
  * `gapless::T3`: The threshold for considering a band as gapless. Default is 0.0.
  * `rounds::T4`: A boolean indicating whether to round a returned variable. Default is true.

# Example

```julia
julia> 
```
