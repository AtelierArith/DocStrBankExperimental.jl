```
leq = LinearEquations{FloatType}(x_names::Vector{String}, x_vec_julia_names::AbstractVector,
                                 x_lengths::Vector{Int}, nx_fixedLength::Int, A_is_constant::Bool;
                                 useRecursiveFactorizationUptoSize = 0)
```

Define linear equation system "A*x=b" with `x::Vector{FloatType}`.

  * `x` is constructed from a set of scalar or vector variables i with names `x_names[i]`  and length `x_length[i]` (that is `length(x) = sum(x_lengths)`). x*names[1:nx*fixedLength] are elements with fixed lengths (dimensions do not change after compilation). x*names[nx*fixedLength+1:end] are vector-valued elements where the dimensions may changer after compilation.
  * `x_vec_julia_names` are the Julia names of the vector-valued elements.
  * If `A_is_constant = true` then `A` is a matrix that is constant after initialization
  * If length(x) <= useRecursiveFactorizationUptoSize, then linear equation systems will be solved with `RecursiveFactorization.jl` instead of the default `lu!(..)` and `ldiv!(..)`.

For details how to use this constructor, see [`LinearEquationsIteration!`](@ref).
