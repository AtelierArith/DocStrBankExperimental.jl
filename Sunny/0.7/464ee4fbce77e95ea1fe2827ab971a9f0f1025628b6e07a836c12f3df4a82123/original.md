```
print_symmetry_table(cryst::Crystal, max_dist)
```

Print symmetry information for all equivalence classes of sites and bonds, up to a maximum bond distance of `max_dist`. Equivalent to calling `print_bond(cryst, b)` for every bond `b` in `reference_bonds(cryst, max_dist)`, where `Bond(i, i, [0,0,0])` refers to a single site `i`.
