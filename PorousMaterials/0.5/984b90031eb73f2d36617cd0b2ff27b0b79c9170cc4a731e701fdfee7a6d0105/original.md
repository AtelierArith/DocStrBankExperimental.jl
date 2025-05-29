```
molecule = ion(q, coords)
```

Facilitate constructing a point charge by constructing a molecule: Molecule(:ion, Atoms{Frac}(0), Charges(q, coords), coords)

# Arguments

  * `q::Float64`: value of point charge, units: electrons
  * `coords::Frac`: fractional coordinates of the charge

# Returns

  * `molecule::Molecule{Frac}`: the ion as a molecule with Fractional coordinates
