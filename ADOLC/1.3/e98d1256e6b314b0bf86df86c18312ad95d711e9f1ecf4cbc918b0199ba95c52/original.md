```
derivative!(
    res,
    f,
    m::Integer,
    n::Integer,
    x::Union{Cdouble,Vector{Cdouble}},
    partials::Vector{Vector{Int64}};
    tape_id::Integer=0,
    reuse_tape::Bool=false,
    id_seed::Bool=false,
    adolc_format::Bool=false,
)
```

A variant of the [`derivative`](@ref) driver for the computation of  [higher-order](@ref "Higher-Order") derivatives that allows the user to provide  a pre-allocated container for the result `res`. In addition to the arguments of  [`derivative`](@ref), the output dimension `m` and input dimension `n` of the function `f` is required. If there is already a valid tape for the function `f` at the  selected point `x` use `reuse_tape=true` and set the `tape_id` accordingly to  avoid the re-creation of the tape.

Example: 

```jldoctest
f(x) = x[1]^4*x[2]*x[3]*x[4]^2
x = [3.0, -1.5, 1.5, -2.0]
partials = [[4, 0, 0, 0], [3, 0, 1, 2]]
m = 1
n = 4
res = CxxMatrix(m, length(partials))
derivative!(res, f, m, n, x, partials)
res

# output

1×2 CxxMatrix:
 -216.0  -216.0
```
