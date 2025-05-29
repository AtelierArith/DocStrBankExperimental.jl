```
MagnetizationMC((x1, y1, z1), ...)
MagnetizationMC{T}(N)
MagnetizationMC(N)
```

Create a `MagnetizationMC` object representing `N` 3D magnetization vectors in the same physical location.

One can access the ith component magnetization vector by indexing the `MagnetizationMC` object. Furthermore, iterating the `MagnetizationMC` object iterates through each of the component magnetization vectors.

# Properties

  * `M::NTuple{N,Magnetization{<:Real}}`: List of component magnetization vectors

# Examples

```jldoctest
julia> M = MagnetizationMC((1, 2, 3), (4, 5, 6))
2-compartment Magnetization vector with eltype Int64:
 Compartment 1:
  Mx = 1
  My = 2
  Mz = 3
 Compartment 2:
  Mx = 4
  My = 5
  Mz = 6

julia> M[2]
Magnetization vector with eltype Int64:
 Mx = 4
 My = 5
 Mz = 6

julia> foreach(m -> (m.x = 0; m.y = 1; m.z = 2), M)

julia> M
2-compartment Magnetization vector with eltype Int64:
 Compartment 1:
  Mx = 0
  My = 1
  Mz = 2
 Compartment 2:
  Mx = 0
  My = 1
  Mz = 2
```
