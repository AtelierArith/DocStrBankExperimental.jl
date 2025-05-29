```julia
struct ReLU <: MIPVerify.Layer
```

Represents a ReLU operation.

`p(x)` is shorthand for [`relu(x)`](@ref) when `p` is an instance of `ReLU`.
