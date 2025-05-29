```
random_reinsertion!(molecule, box)
```

Perform a translation and rotated (if needed) on a molecule, and keep a copy of the original in case it needs to be restored.

# Arguements

  * `molecule::Molecule{Frac}`: molecule to be translated and rotated (if needed)
  * `box::Box`: the box used in rotation

# Returns

  * `old_molecule::Molecule{Frac}`: a copy of the original molecule
