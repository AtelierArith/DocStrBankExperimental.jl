```
udgrade(input_map::HealpixMap{T,O,AA}, output_nside; kw...) where {T,O,AA} -> HealpixMap{T,O,AA}
```

Upgrades or downgrades a map to a target nside. Always makes a copy. This is very fast for nested orderings, but slow for ring because one needs to transform to nested ordering first.

# Arguments:

  * `input_map::HealpixMap{T,O,AA}`: the map to upgrade/downgrade
  * `output_nside`: desired nside

# Keywords:

  * `threshold=abs(1e-6UNSEEN)`: absolute tolerance for identifying a bad pixel vs UNSEEN
  * `pess=false`: if false, estimate pixels from remaining good pixels when downgrading.   if true, the entire downgraded pixel is set to UNSEEN.

# Returns:

  * `HealpixMap{T,O,AA}`: upgraded/downgraded map in the same ordering as the input

# Examples

```julia-repl
julia> A = HealpixMap{Float64, NestedOrder}(ones(nside2npix(4)))
192-element HealpixMap{Float64, RingOrder, Vector{Float64}}:
 1.0
 ⋮
 1.0

julia> Healpix.udgrade(A, 2)
48-element HealpixMap{Float64, NestedOrder, Vector{Float64}}:
 1.0
 ⋮
 1.0
```
