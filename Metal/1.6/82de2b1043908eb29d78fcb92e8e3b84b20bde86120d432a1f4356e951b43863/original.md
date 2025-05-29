```
mtl(A; storage=Metal.PrivateStorage)
```

`storage` can be `Metal.PrivateStorage` (default), `Metal.SharedStorage`, or `Metal.ManagedStorage`.

Opinionated GPU array adaptor, which may alter the element type `T` of arrays:

  * For `T<:AbstractFloat`, it makes a `MtlArray{Float32}` for performance and compatibility reasons (except for `Float16`).
  * For `T<:Complex{<:AbstractFloat}` it makes a `MtlArray{ComplexF32}`.
  * For other `isbitstype(T)`, it makes a `MtlArray{T}`.

By contrast, `MtlArray(A)` never changes the element type.

Uses Adapt.jl to act inside some wrapper structs.

# Examples

```jldoctests
julia> mtl(ones(3)')
1×3 adjoint(::MtlVector{Float32, Metal.PrivateStorage}) with eltype Float32:
 1.0  1.0  1.0

julia> mtl(zeros(1,3); storage=Metal.SharedStorage)
1×3 MtlMatrix{Float32, Metal.SharedStorage}:
 0.0  0.0  0.0

julia> mtl(1:3)
1:3

julia> MtlArray(1:3)
3-element MtlVector{Int64, Metal.PrivateStorage}:
 1
 2
 3
```
