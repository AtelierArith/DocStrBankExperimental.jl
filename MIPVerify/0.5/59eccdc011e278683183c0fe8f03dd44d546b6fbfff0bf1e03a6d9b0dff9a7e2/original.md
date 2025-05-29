```julia
struct Pool{N} <: MIPVerify.Layer
```

Represents a pooling operation.

`p(x)` is shorthand for [`pool(x, p)`](@ref) when `p` is an instance of `Pool`.

## Fields:

  * `strides`
  * `pooling_function`
