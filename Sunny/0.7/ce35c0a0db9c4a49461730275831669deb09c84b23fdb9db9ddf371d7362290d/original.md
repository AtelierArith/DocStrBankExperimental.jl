```
reference_bonds(cryst::Crystal, max_dist)
```

Returns a full list of bonds, one for each symmetry equivalence class, up to distance `max_dist`. The reference bond `b` for each equivalence class is selected according to a scoring system that prioritizes simplification of the elements in `basis_for_symmetry_allowed_couplings(cryst, b)`.
