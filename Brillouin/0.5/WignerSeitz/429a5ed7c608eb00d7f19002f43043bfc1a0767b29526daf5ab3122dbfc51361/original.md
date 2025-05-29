```
in_wignerseitz(v::AbstractVector{<:AbstractVector{<:Real}}, c::Cell)  -->  BitVector
```

For a list of points `vs`, return whether each of the points are inside the Wigner-Seitz cell `c`. 

See also `in_wigner_seitz(v::AbstractVector(<:Real), c::Cell)`.
