```
wombling(x::Vector{T}, y::Vector{T}, z::Matrix{T}) where {T<:Number}
```

Wrapper function that implements the lattice wombling algorithm for points that are regularly arranged in space. Note that the matrix is presented in a way that is flipped, *i.e.* the `x` coordinates corresponds to the rows, and the `y` coordinates correspond to the columns. If you want to think of `x` and `y` as geographic coordinates, `y` are the longitudes, and `x` are the latitudes. Using the bindings for `SimpleSDMLayers`, this conversion will be performed automatically.
