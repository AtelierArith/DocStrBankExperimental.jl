```
is_isomorphic(candidate::FGVertexCandidate, fgv::FGVertex; kwargs...) -> Bool
```

Return `true` if `candidate` is in the isotopy class of `fgv`. 

# Arguments

  * `labeled_points :: Bool = true` : If is set to `false`, then the isomorphism would also allow a relabeling of the points.
