```
mutable struct VDimensions{T, S}
```

A mutable struct representing the right dimensions for an object that can be shown on a plot using Plots.jl or Makie.jl.

# Fields

  * `xs::Vector{T}`: A vector containing the x-coordinates.
  * `ys::Vector{S}`: A vector containing the y-coordinates.
  * `labels::Labels{T, S}`: An instance of `Labels` containing labels for the x and y coordinates.
  * `minor_lines::Vector{T}`: A vector containing the positions of minor extension lines.
  * `major_lines::Vector{T}`: A vector containing the positions of major extension lines.
  * `offset::T`: Stores the offset value of the dimension

# Type Parameters

  * `T`: The type of the elements in the `xs`, `minor_lines`, `major_lines` vectors and `offset` value.
  * `S`: The type of the elements in the `ys` vector.
