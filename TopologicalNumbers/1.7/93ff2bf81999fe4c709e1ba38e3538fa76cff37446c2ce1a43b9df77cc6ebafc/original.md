```
WPProblem{T1<:Function,T2<:Int,T3<:AbstractVector,T4<:Bool} <: TopologicalNumbersProblems
```

A struct representing a problem for calculating the Weyl points.

# Fields

  * `H::T1`: The Hamiltonian function `H=H(k)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector. Dimension of `k` must be 3.
  * `N::T2`: The number of meshes when discretizing the Brillouin Zone. The $n$th iteration divides the Brillouin zone into $1/N^n$. Default is 10.
  * `gapless::T3` The threshold that determines the state to be degenerate. The $n$th iteration adopts the threshold value of the $n$th value of the vector. The number of iterations can be varied by the length of the vector. Default is `[1e-1, 1e-2, 1e-3, 1e-4]`.
  * `rounds::T4`: A boolean indicating whether to round a returned variable. Default is true.

# Example

```julia
julia> 
```
