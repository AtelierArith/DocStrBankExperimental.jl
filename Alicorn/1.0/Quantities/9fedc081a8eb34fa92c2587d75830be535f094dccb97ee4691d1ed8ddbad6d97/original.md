```
QuantityArray{T<:Number,N} <: AbstractQuantityArray{T,N}
```

A physical quantity consisting of an array, a `Dimension` object representing the physical dimension, and an `InternalUnits` object representing the units with respect to which the seven basic dimensions of the SI system are measured.

The value field of a `QuantityArray{T,N}` is of type `Array{T,N}`. `T` needs to be a subtype of `Number`.

# Fields

  * `value::Array{T,N}`: value of the quantity
  * `dimension::Dimension`: physical dimension of the quantity
  * `internalUnits::InternalUnits`: set of units with respect to which the seven

basic dimensions of the SI system are measured.

# Constructors

```
QuantityArray(::AbstractArray, ::Dimension, ::InternalUnits)
QuantityArray(::AbstractArray, ::Dimension)
QuantityArray(::AbstractArray, ::InternalUnits)
QuantityArray(::AbstractArray)
```

If no `InternalUnits` are passed to the constructor, the basic SI units are used. If no `Dimension` is passed to the constructor, a dimensionless quantity is constructed.

```
QuantityArray{T}(::AbstractArray, ::Dimension, ::InternalUnits) where {T<:Number}
QuantityArray{T}(::AbstractArray, ::Dimension) where {T<:Number}
QuantityArray{T}(::AbstractArray, ::InternalUnits) where {T<:Number}
QuantityArray{T}(::AbstractArray) where {T<:Number}
```

If the type `T` is specified explicitly, Alicorn attempts to convert the provided `AbstractArray` to `Array{T}`.
