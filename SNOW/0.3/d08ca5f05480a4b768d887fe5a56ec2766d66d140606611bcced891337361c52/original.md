```
SparsePattern(diffmethod, func!, ng, lx, ux)
```

detect sparsity pattern by computing derivatives  at three randomly generating locations w/in bounds.  Entries that are zero at all three spots are assumed to always be zero.

# Arguments

  * `diffmethod::AbstractDiffMethod`: method to compute derivatives
  * `func!::Function`: function of form f = func!(g, x)
  * `ng::Int`: number of constraints
  * `lx::Vector{Float}`: lower bounds on x
  * `ux::Vector{Float}`: upper bounds on x
