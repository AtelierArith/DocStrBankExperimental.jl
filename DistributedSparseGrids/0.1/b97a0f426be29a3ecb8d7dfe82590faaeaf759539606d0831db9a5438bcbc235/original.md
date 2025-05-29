```
interpolate(asg::SG, x::VCT, stplvl::Int=numlevels(asg))
```

Interpolate at position `x`. 

# Arguments

  * `asg::SG<:AbstractHierarchicalSparseGrid{N,HCP}}`: initialized adaptive sparse grid
  * `cpts::Dict{SVector{N,Int},Dict{SVector{N,Int},HCP}}`: Dict cointaining all collocation points
