```
IdentityMultiple{T} < AbstractMatrix{T} where T
```

A scalar multiple of the identity matrix of given order and numeric type.

### Fields

  * `M` – uniform scaling operator of type `T`
  * `n` – size of the identity matrix

### Notes

This type can be used to create multiples of the identity of given size. Since only the multiple and the order are stored, the allocations are minimal.

Internally, the type wraps Julia's lazy multiple of the identity operator, `UniformScaling`. `IdentityMultiple` subtypes `AbstractMatrix`, hence it can be used in usual matrix arithmetic and for dispatch on `AbstractMatrix`.

The difference between `UniformScaling` and `IdentityMultiple` is that while the size of the former is generic, the size of the latter is fixed.

### Examples

Only specifying the matrix size represents an identity matrix:

```jldoctest identitymultiple
julia> using MathematicalSystems: IdentityMultiple

julia> I2 = Id(2)
IdentityMultiple{Float64} of value 1.0 and order 2

julia> I2 + I2
IdentityMultiple{Float64} of value 2.0 and order 2

julia> 4*I2
IdentityMultiple{Float64} of value 4.0 and order 2
```

The scaling (default `1.0`) can be passed as the second argument:

```jldoctest identitymultiple
julia> I2r = Id(2, 1//1)
IdentityMultiple{Rational{Int64}} of value 1//1 and order 2

julia> I2r + I2r
IdentityMultiple{Rational{Int64}} of value 2//1 and order 2

julia> 4*I2r
IdentityMultiple{Rational{Int64}} of value 4//1 and order 2
```

Alternatively, use the constructor passing the `UniformScaling` (`I`):

```jldoctest identitymultiple
julia> using LinearAlgebra

julia> I2 = IdentityMultiple(2.0*I, 2)
IdentityMultiple{Float64} of value 2.0 and order 2

julia> I2r = IdentityMultiple(2//1*I, 2)
IdentityMultiple{Rational{Int64}} of value 2//1 and order 2
```
