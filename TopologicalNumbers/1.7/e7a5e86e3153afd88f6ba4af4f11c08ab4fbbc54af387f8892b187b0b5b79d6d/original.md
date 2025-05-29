```
WCSProblem{T1<:Function,T2<:String,T3<:Int,T4<:Union{Tuple,AbstractVector,Int},T5<:Real,T6<:Bool} <: TopologicalNumbersProblems
```

A struct representing a problem for finding and calculating the Weyl points.

# Fields

  * `H::T1`: The Hamiltonian function `H=H(k)` that defines the system. `k` is a abstract vector (or a tuple) of the wavenumber vector. Dimension of `k` must be 3.
  * `kn::T2`: Compute the Chern number of the plane perpendicular to the `"kn"` direction in Brillouin zone (`"k1"`, `"k2"`, `"k3"`).
  * `kn_mesh::T3`: Number of mesh in `"kn"` direction. Default is 51.
  * `N::T4`: The number of points for one direction in the Brillouin zone. Default is 51.
  * `gapless::T5`: The threshold for considering a band as gapless. Default is 0.0.
  * `rounds::T6`: A boolean indicating whether to round a returned variable. Default is true.

# Example

```julia
julia> 
```
