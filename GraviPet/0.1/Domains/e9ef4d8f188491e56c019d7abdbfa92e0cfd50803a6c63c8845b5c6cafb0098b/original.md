```
abstract type Domain{T}
```

A computational domain of type `T`. The *domain* of a function is the type of its argument(s). For example, `Domain{Float64}` would describe a one-dimensional domain, and `Domain{SVector{3,Float64}}` would describe a three-dimensional domain.

This type can also describe a codomain, i.e. the result type of a function. A codomain of `Domain{Float64}` describes a scalar function, and a codomain of `Domain{SVector{3,Float64}}` describes a vector-valued function.

See also [`Interval`](#GraviPet.Intervals.Interval) and [`Box`](#GraviPet.Boxes.Box) for concrete domain types.
