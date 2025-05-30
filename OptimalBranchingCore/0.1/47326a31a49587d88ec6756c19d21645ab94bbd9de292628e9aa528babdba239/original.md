```
covered_by(t::BranchingTable, dnf::DNF)
```

Check if the branching table `t` is covered by the logic expression `dnf`. Returns `true` if there exists at least one bitstring in each group of `t` that satisfies `dnf`, `false` otherwise.
