```
struct LocalOperator{T,G}
```

`N`-body operator acting on `N` sites, indexed through lattice points of type `G`. The operator is represented as a vector of `MPOTens, instantiate_operatoror`s, each of which acts on a single site.

# Fields

  * `opp::Vector{T}`: `N`-body operator represented by an MPO.
  * `inds::Vector{G}`: `N` site indices.
