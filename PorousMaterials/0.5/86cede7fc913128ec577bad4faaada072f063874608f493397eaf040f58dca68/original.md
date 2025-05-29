```
random_reinsertion!(molecule, box)
```

Perform a translational perturbation in Cartesian coordinates on a molecule, apply the periodic boundry conditions, and keep a copy of the original in case it needs to be restored.

# Arguements

  * `molecule::Molecule{Frac}`: molecule to be translated
  * `box::Box`: the box used in rotation

# Returns

  * `old_molecule::Molecule{Frac}`: a copy of the original molecule
