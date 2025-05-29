```
derivative(
    f::Function,
    x::Union{Cdouble,Vector{Cdouble}},
    param::Union{Cdouble,Vector{Cdouble}},
    mode::Symbol;
    dir=Vector{Cdouble}(),
    weights=Vector{Cdouble}(),
    tape_id::Integer=0,
    reuse_tape::Bool=false,
)
```

This version of the [`derivative`](@ref) driver allows the definition of function parameters (`param`), which can be changed  in subsequent calls without retaping. The given function `f` is expected to have the shape `f(x, param)`.

# Example:

```jldoctest
function f(x, param)
    x1 = x[1] * param[1]
    return [x1*x[2], x[2]] 
end
x = [-1.0, 1/2]
param = 3.0
dir = [2.0, -2.0]
res = derivative(f, x, param, :jac_vec, dir=dir, tape_id=1)

##res[1] == 9.0
##res[2] == -2.0

param = -3.0
x = [1.0, 1.0]
res = derivative(f, x, param, :jac_vec, dir=dir, tape_id=1, reuse_tape=true)
res 

# output

2-element CxxVector:
  0.0
 -2.0
```
