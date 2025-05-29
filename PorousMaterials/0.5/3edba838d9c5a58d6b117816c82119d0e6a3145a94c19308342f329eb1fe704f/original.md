```
is_distorted = distortion(molecule, ref_molecule, box; 
                          atol=1e-12, throw_warning=true)
```

Determine whether a molecule has distortion w.r.t. a reference molecule via pairwise distance comparison of the atoms and charges coordinates.

# Arguments

  * `molecule::Molecule{Frac}`: molecule you want to compare
  * `ref_molecule::Molecule{Frac}`: reference molecule
  * `box::Box`: box used for the fractional coordinates
  * `atol::Float64=1e-12`: absolute tolerance for distance comparison
  * `throw_warning::Bool=true`: issue a warning if there is distortion

# Returns

  * `is_distorted::Bool`: true if there is distortion w.r.t. reference molecule
