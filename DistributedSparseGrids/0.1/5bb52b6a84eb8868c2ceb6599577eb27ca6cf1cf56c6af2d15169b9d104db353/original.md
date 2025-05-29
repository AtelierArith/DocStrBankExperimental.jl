```
integrate(asg::SG) where {N,CP,RT,HCP<:AbstractHierarchicalCollocationPoint{N,CP,RT}, SG<:AbstractHierarchicalSparseGrid{N,HCP}}
```

Integrates the sparse grid. Returns an instance of RT.

# Constructor

  * `asg::SG`: adaptie sparse grid
