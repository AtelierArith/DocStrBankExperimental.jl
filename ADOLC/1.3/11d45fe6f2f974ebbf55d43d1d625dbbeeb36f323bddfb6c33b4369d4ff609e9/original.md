```
derivative!(
    res,
    f::Function,
    m::Integer,
    n::Integer,
    x::Union{Cdouble,Vector{Cdouble}},
    mode::Symbol;
    dir::Union{Vector{Cdouble},Matrix{Cdouble}}=Vector{Cdouble}(),
    weights::Union{Vector{Cdouble},Matrix{Cdouble}}=Vector{Cdouble}(),
    tape_id::Integer=0,
    reuse_tape::Bool=false,
)
```

A variant of the [`derivative`](@ref) driver for [first-](@ref "First-Order"), [second-order](@ref "Second-Order") and [abs-normal-form](@ref "Abs-Normal-Form")  computations that allows the user to provide a pre-allocated container for the result `res`. The container can be allocated by leveraging the methods [`allocator`](@ref) or [`init_abs_normal_form`](@ref). In addition to the arguments of [`derivative`](@ref), the output dimension `m` and  input dimension `n` of the function `f` is required. If there is already a valid  tape for the function `f` at the selected point `x` use `reuse_tape=true` and set the `tape_id` accordingly to avoid the re-creation of the tape.

Example:

```jldoctest
f(x) = [cos(x[1]), x[2]*x[3]]
x = [0.0, 1.5, -1.0]
mode = :hess_mat
dir = [[1.0, -1.0, 1.0] [0.5, -0.5, 1.0]]
m = 2
n = 3
res =  allocator(m, n, mode, size(dir, 2)[1], 0)
derivative!(res, f, m, n, x, mode, dir=dir)
res
# output

2×3×2 CxxTensor:
[:, :, 1] =
 -1.0  0.0   0.0
  0.0  1.0  -1.0

[:, :, 2] =
 -0.5  0.0   0.0
  0.0  1.0  -0.5
```

```jldoctest
f(x) = max(x[1]*x[2], x[1]^2)
x = [1.0, 1.0]
m = 1
n = 2
abs_normal_form = init_abs_normal_form(f, x)
derivative!(abs_normal_form, f, m, n, x, :abs_normal, tape_id=abs_normal_form.tape_id, reuse_tape=true)
abs_normal_form
# output

AbsNormalForm(0, 1, 2, 1, [1.0, 1.0], [1.0], [0.0], [0.0], [1.0], [1.5 0.5], [0.5;;], [1.0 -1.0], [0.0;;])
```
