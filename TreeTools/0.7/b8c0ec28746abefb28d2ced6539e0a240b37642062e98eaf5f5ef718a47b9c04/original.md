```
newick(tree::Tree; internal_labels=true, write_root=true)
```

Return the Newick string correpsonding to `tree`. If `internal_labels == false`, do not write labels of internal nodes in the string. If `!write_root`, do not write label and time for the root node (unrooted tree).
