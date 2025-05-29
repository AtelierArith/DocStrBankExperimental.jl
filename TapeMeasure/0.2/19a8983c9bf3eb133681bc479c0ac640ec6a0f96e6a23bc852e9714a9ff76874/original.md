```
mutable struct Labels{T, S}
```

A structure to hold labeled information for dimensions object.

# Fields

  * `xs::Vector{T}`: A vector of x-coordinates of type `T`.
  * `ys::Vector{S}`: A vector of y-coordinates of type `S`.
  * `lbls::Vector{String}`: A vector of labels corresponding to the data points.
