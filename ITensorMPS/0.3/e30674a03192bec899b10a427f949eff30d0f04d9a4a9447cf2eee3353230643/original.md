```
truncate!(M::MPS; kwargs...)
truncate!(M::MPO; kwargs...)
```

Perform a truncation of all bonds of an MPS/MPO, using the truncation parameters (cutoff,maxdim, etc.) provided as keyword arguments.

Keyword arguments:

  * `site_range`=1:N - only truncate the MPS bonds between these sites
  * `callback=Returns(nothing)` - callback function that allows the user to save the per-bond truncation error. The API of `callback` expects to take two kwargs called `link` and `truncation_error` where `link` is of type `Pair{Int64, Int64}` and `truncation_error` is `Float64`. Consider the following example that illustrates one possible use case.

```julia
nbonds = 9
truncation_errors = zeros(nbonds)
function callback(; link, truncation_error)
  bond_no = last(link)
  truncation_errors[bond_no] = truncation_error
  return nothing
end
truncate!(ψ; maxdim=5, cutoff=1E-7, callback)
```
