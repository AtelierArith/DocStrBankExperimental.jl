```
XPRS_HEURSEARCHTREESELECT
```

A bit vector control for selecting which local search heuristics to apply during the tree search of a MIP solve. (integer)

Use HEURSEARCHROOTSELECT to control local search heuristics on the root node.

Default value: `17`

Values are a bitset: bit 0 : Local search with a large neighborhood. Potentially slow but is good for finding solutions that differs significantly from the incumbent. bit 1 : Local search with a small neighborhood centered around a node LP solution. bit 2 : Local search with a small neighborhood centered around an integer solution. This heuristic will often provide smaller, incremental improvements to an incumbent solution. bit 3 : Local search with a neighborhood set up through the combination of multiple integer solutions. bit 4 : Unused bit 5 : Local search without an objective function. Called seldom and only when no feasible solution is available. bit 6 : Local search with an auxiliary objective function. Called seldom and only when no feasible solution is available.
