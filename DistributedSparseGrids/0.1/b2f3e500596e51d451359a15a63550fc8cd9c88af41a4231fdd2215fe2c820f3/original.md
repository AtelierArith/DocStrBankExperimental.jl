```
init(::Type{AHSG{N,HCP}}, pointSetProperties::SVector{N,Int})
```

Initialize the sparse grid. Returns a `N`-dimensional sparse grid where only the root point has been created.

# Constructor

  * `::Type{AHSG{N,HCP}}`: Define type of [`DistributedSparseGrids.ASHG`](@ref)
  * `pointSetProperties::SVector{N,Int}`: Vector containing all pointset properties.

Pointset properties = [psp*1,...,psp*N], psp_i in [1,2,3,4].  1=>`closed point set`,  2=>`open point set`,  3=>`left-open point set`,  4=>`right-open point set.`

# Example

N = 1; pointprobs = @SVector [1]; RT = Float64; CT = Float64; CPType = CollocationPoint{N,CT}; HCPType = HierarchicalCollocationPoint{N,CPType,RT}; asg = init(AHSG{N,HCPType},pointprobs)
