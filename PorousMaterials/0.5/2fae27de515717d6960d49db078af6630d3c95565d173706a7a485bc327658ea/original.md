```
apply_periodic_boundary_condition!(molecule::Molecule{Frac})
```

Check if each of a molecule's center-of-mass coordinates is within the bounds (0.0, 1.0) in fractional coordinates, and translate if needed.

# Arguments

  * `molecule::Molecule{Frac}`: the molecule to be checked

# Returns

  * `nothing`, if the molecule is within the boundary; ohterwise, the coordinates of the input molecule will be modified
