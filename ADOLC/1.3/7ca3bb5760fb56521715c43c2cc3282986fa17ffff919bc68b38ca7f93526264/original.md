```
derivative(
    f::Function,
    x::Union{Cdouble,Vector{Cdouble}},
    partials::Vector{Vector{Int64}};
    tape_id::Integer=0,
    reuse_tape::Bool=false,
    id_seed::Bool=false,
    adolc_format::Bool=false,
)
```

A variant of the [`derivative`](@ref) driver, which can be used to compute [higher-order](@ref "Higher-Order") derivatives of the function `f`  at the point `x`. The derivatives are specified as mixed-partials in the `partials` vector. To define the partial-derivatives use either the [Partial-Format](@ref) or the [ADOLC-Format](@ref) and set `adolc_format` accordingly. The flag `id_seed` is used to specify the method for [seed-matrix generation](@ref "Seed-Matrix"). The underlying method leverages a tape, which has the identifier `tape_id`. If there is already a valid  tape for the function `f` at the selected point `x` use `reuse_tape=true` and set the `tape_id` accordingly to avoid the re-creation of the tape.

# Examples:

Partial-Format:

```jldoctest
f(x) = [x[1]^2*x[2]^2, x[3]^2*x[4]^2]
x = [1.0, 2.0, 3.0, 4.0]
partials = [[1, 1, 0, 0], [0, 0, 1, 1], [2, 2, 0, 0]]
res = derivative(f, x, partials)

# output

2×3 CxxMatrix:
 8.0   0.0  4.0
 0.0  48.0  0.0
```

ADOLC-Format:

```jldoctest
f(x) = [x[1]^2*x[2]^2, x[3]^2*x[4]^2]
x = [1.0, 2.0, 3.0, 4.0]
partials = [[2, 1, 0, 0], [4, 3, 0, 0], [2, 2, 1, 1]]
res = derivative(f, x, partials, adolc_format=true)

# output

2×3 CxxMatrix:
 8.0   0.0  4.0
 0.0  48.0  0.0
```
