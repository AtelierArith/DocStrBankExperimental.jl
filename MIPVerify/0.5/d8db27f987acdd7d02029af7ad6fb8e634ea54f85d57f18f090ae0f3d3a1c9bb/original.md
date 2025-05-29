```julia
struct MaskedReLU{T<:Real} <: MIPVerify.Layer
```

Represents a masked ReLU activation, with `mask` controlling how the ReLU is applied to each output.

`p(x)` is shorthand for [`masked_relu(x, p.mask)`](@ref) when `p` is an instance of `MaskedReLU`.

## Fields:

  * `mask`
  * `tightening_algorithm`
