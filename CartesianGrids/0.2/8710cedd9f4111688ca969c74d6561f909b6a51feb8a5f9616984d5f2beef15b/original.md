```
TensorData <: PointData
```

A wrapper for a one-dimensional array of 2x2 tensor-valued data, with fields `dudx`, `dudy`, `dvdx`, `dvdy`. The resulting wrapper can be indexed as though these four components are stacked on top of each other.

# Constructors

  * `TensorData(d::AbstractVector[,dtype=Float64])` constructs a wrapper for the one-dimensional array of data `d`, splitting `d` into the four components evenly.
  * `TensorData(dudx,dudy,dvdx,dvdy)` constructs a wrapper for the tensor components data, each of type `AbstractVector`
  * `TensorData(n::Int)` constructs a wrapper with zeros of length `n` for all components.
  * `TensorData(x::PointData[,dtype=Float64])` constructs a wrapper for zero components of the  same length as that wrapped by `x`.

# Example
