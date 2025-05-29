```
derivative!(
    res,
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

This version of the [`derivative!`](@ref) driver allows the definition of function parameters (`param`), which can be changed  in subsequent calls without retaping. The given function `f` is expected to have the shape `f(x, param)`.

# Example:

```jldoctest
function f(x, param)
    a = x*param
    return a^2
end
x = 3.0
param = -1.0
tape_id = 0
m = n = 1
res = CxxVector(1)
derivative!(res, f, m, n, x, param, :jac, tape_id=tape_id)
##res[1] = 6.0

param = -4.5
derivative!(res, f, m, n, x, param, :jac, reuse_tape=true, tape_id=tape_id)
res

# output

1-element CxxVector:
 121.5
```
