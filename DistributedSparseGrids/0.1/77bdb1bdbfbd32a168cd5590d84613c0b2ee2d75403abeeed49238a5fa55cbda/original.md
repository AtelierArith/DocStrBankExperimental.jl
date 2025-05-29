```
generate_next_level!(asg::AHSG{N,HCP}, tol::CT,maxlvl::Int) where {N,CT,CP<:AbstractCollocationPoint{N,CT},HCP<:AbstractHierarchicalCollocationPoint{N,CP}}
```

Adaptively generate all collocation point of the next hierarchical level, where `norm(scaling_weight(cpt)) > tol && level(cpt)<maxlvl`.

# Constructor

  * `asg::AHSG{N,HCP}`: sparse grid
  * `tol::CT`: tolerance
  * `maxlvl::Int`: maximum hierarchical level
