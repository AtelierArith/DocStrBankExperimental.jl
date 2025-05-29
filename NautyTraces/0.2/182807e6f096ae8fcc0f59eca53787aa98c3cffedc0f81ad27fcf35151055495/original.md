```
nauty(g::DenseNauty[Di]Graph; getcanon = false, automgroup = false, partition = nothing) -> NAUTY
```

nauty is a higher-level interface to nauty, which relies on densenauty. The arguments are a graph `g` and optional named arguments getcanon::Bool, automgroup::Bool and partition, which is either `nothing` or a tuple `(lab,ptn)` as in the raw Nauty format, or a list of lists of vertices (numbered from 1).

The return value is a mutable struct NAUTY with entries

  * `orbits::IntDisjointSet`, the orbits of the automorphism group numbered from 1
  * `grpsize::BigInt`, the group size (possibly with rounding errors)
  * if automgroup, `generators::Vector{Tuple{Permutation,IntDisjointSets,Int}}, the generators of the automorphism group, representing each generator with the orbits under the generators up to this one and the stabilized vertex up to now
  * if getcanon, `lab::Permutation`, the correspondence between old vertices and new ones, and `canong::typeof(g)`, the canonically labelled graph
