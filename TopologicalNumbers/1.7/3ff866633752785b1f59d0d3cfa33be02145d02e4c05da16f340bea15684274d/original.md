```
WNProblem{T1<:Function,T2<:AbstractVector,T3<:Int,T4<:Real,T5<:Bool} <: TopologicalNumbersProblems
```

A struct representing a problem for calculating the Weyl nodes.

# Fields

  * `H::T1`: The Hamiltonian function `H=H(k)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector. Dimension of `k` must be 3.
  * `n::T2`: An `AbstractVector` (or a `Tuple`) including two elements of `Int`, which represents wavenumber ($2\pi n/N$). Dimension of `n` must be 3.
  * `N::T3`: The number of points for one direction in the Brillouin zone. Default is 51.
  * `gapless::T4`: The threshold for considering a band as gapless. Default is 0.0.
  * `rounds::T5`: A boolean indicating whether to round a returned variable. Default is true.

# Example

```julia
julia> 
```
