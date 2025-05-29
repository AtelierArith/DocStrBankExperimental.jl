```
LBFProblem{T1<:Function,T2<:AbstractVector,T3<:Union{Tuple,AbstractVector,Int},T4<:Real,T5<:Bool} <: TopologicalNumbersProblems
```

A struct representing a problem for calculating the $k$-local value of Berry flux.

# Fields

  * `H::T1`: The Hamiltonian function `H=H(k)` that defines the system. `k` is an `AbstractVector` (or a `Tuple`) of the wavenumber vector. Dimension of `k` must be 2.
  * `n::T2`: An `AbstractVector` (or a `Tuple`) including two elements of `Int`, which represents wavenumber ($2\pi n/N$) when calculating Berry flux. Dimension of `n` must be 2.
  * `N::T3`: The number of points for one direction in the Brillouin zone. Default is 51.
  * `gapless::T4`: The threshold for considering a band as gapless. Default is 0.0.
  * `rounds::T5`: A boolean indicating whether to round a returned variable. Default is true.

# Example

```julia
julia> 
```
