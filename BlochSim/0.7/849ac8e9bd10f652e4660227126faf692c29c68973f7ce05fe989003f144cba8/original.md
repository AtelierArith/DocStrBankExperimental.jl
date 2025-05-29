```
ExcitationMatrix(A)
ExcitationMatrix{T}()
ExcitationMatrix()
```

Create an `ExcitationMatrix` object. Multiplying by a `MagnetizationMC` object has the effect of multiplying each component of the multi-compartment magnetization by the `ExcitationMatrix`.

# Properties

  * `A::BlochMatrix{<:Real}`: Matrix used to describe the excitation

# Examples

```jldoctest
julia> E = ExcitationMatrix(BlochMatrix(0, 1, 0, 1, 0, 0, 0, 0, 1))
ExcitationMatrix{Int64}:
 0  1  0
 1  0  0
 0  0  1

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

julia> E * M
2-compartment Magnetization vector with eltype Int64:
 Compartment 1:
  Mx = 2
  My = 1
  Mz = 3
 Compartment 2:
  Mx = 5
  My = 4
  Mz = 6
```
