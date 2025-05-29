```
compliance_matrix(nodes, elements; cache=initialize_cache(nodes, elements),
    gxbeam_order=true, shear_center=true)
```

Compute compliance matrix given a finite element mesh described by nodes and elements.

# Arguments

  * `nodes`: Vector containing all the nodes in the mesh
  * `elements`: Vector containing all the elements in the mesh
  * `cache::SectionCache`: A pre-allocated cache which may be passed in to reduce allocations   across multiple calls to this function when the number of nodes, number of elements, and   connectivity remain the same.
  * `gxbeam_order::Bool`: Indicates whether the compliance matrix should be provided in the   order expected by GXBeam (rather than the internal ordering used by the section analysis)
  * `shear_center::Bool`: Indicates whether the compliance matrix should be provided about the   shear center

# Returns

  * `S::Matrix`: compliance matrix
  * `sc::Vector{float}`: x, y location of shear center (location where a transverse/shear   force will not produce any torsion, i.e., beam will not twist)
  * `tc::Vector{float}`: x, y location of tension center, aka elastic center, aka centroid   (location where an axial force will not produce any bending, i.e., beam will remain   straight)
