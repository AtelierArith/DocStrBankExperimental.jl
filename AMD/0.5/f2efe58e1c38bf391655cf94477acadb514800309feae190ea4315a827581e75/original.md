Base type to hold control and information related to a call to AMD. `control` is a `Vector{Float64}` with components:

  * d = control[AMD_DENSE]: rows with more than max(d√n, 16) entries are considered "dense" and appear last in the permutation.

If d < 0 no row will be treated as dense.

  * control[AMD_AGGRESSIVE]: triggers aggressive absorption if nonzero.

`info` is a `Vector{Float64}` that contains statistics on the ordering.
