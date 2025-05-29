```
getnodeheights_average(net, checkpreorder::Bool=true; warn=true)
```

Vector of average node heights, that is: the average distance from the root to each node. The average is a weighted average with weights taken to be the hybrid edges' inheritance values γ, if available. Equal weights are used at hybrid nodes with some parents lacking a γ inheritance value (with a warning).

missing edge lengths:

  * An error is thrown if a tree edge has a missing edge length.
  * If all parent hybrid edges have missing lengths at a given hybrid node, then the hybrid node is assumed to be as close to the root as possible, that is, the reticulation is assumed "zipped-up" with one of its hybrid edges of length 0.
  * If some but not all parent hybrid edges have a missing length, then the average node height is calculated based on the non-missing parents only. If the hybrid node height turns out to be lower than one of the parent's height (such that some missing length would need to be negative) then a warning is issued.

A warning is issued, unless `warn=false`, if the network is not time-consistent.

See also: [`istimeconsistent`](@ref), [`getnodeheights`](@ref), and `getnodeheights_majortree`](@ref).
