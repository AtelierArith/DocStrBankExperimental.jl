```
SimpleQuantityArray{T<:Number,N} <: AbstractQuantityArray{T,N}
```

A physical quantity consisting of a number array and a physical unit.

The value field of a `SimpleQuantityArray{T,N}` is of type `Array{T,N}`. `T` needs to be a subtype of `Number`.

# Fields

  * `value::Array{T,N}`: value of the quantity
  * `unit::Unit`: unit of the quantity

# Constructors

```
SimpleQuantityArray(::AbstractArray, ::AbstractUnit)
SimpleQuantityArray(::AbstractArray)
```

If no unit is passed to the constructor, `unitlessUnit` is used by default.

```
SimpleQuantityArray{T}(::AbstractArray, ::AbstractUnit) where {T<:Number}
SimpleQuantityArray{T}(::AbstractArray) where {T<:Number}
```

If the type `T` is specified explicitly, Alicorn attempts to convert the `value` accordingly.
