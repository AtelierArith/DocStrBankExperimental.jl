```
AffineTransform
```

A type representing an affine transfomration that can be used to convert values from one unit to another. This is the output type of `uconvert(u::AbstractUnitLike, u0::AbstractUnitLike)`. This object is callable.

# Fields

  * scale :: Float64
  * offset :: Float64

# Constructors

  * AffineTransform(scale::Real, offset::Real)
  * AffineTransform(; scale, offset)
