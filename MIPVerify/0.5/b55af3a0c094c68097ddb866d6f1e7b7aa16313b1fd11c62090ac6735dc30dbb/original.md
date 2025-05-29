```julia
struct Conv2d{T<:Union{Real, JuMP.VariableRef, JuMP.AffExpr}, U<:Union{Real, JuMP.VariableRef, JuMP.AffExpr}, V<:Integer} <: MIPVerify.Layer
```

Represents 2-D convolution operation.

`p(x)` is shorthand for [`conv2d(x, p)`](@ref) when `p` is an instance of `Conv2d`.

## Fields:

  * `filter`
  * `bias`
  * `stride`
  * `padding`
