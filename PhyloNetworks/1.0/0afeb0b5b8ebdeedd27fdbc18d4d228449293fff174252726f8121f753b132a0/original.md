```
writesubtree!(IO, network, dendroscope::Bool, namelabel::Bool,
              round_branch_lengths::Bool, digits::Integer,
              internallabel::Bool)
```

Write to IO the extended newick format (parenthetical description) of a network. If written for dendroscope, inheritance γ's are not written. If `namelabel` is true, taxa are labelled by their names; otherwise taxa are labelled by their number IDs. If unspecified, branch lengths and γ's are rounded to 3 digits. Use `internallabel=false` to suppress the labels of internal nodes.
