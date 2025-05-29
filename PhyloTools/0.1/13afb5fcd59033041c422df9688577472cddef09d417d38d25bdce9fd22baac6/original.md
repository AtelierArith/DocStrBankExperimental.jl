```
readnw(s::AbstractString, I::Type)
```

Read a newick string to a tree. Supports the original Newick standard (http://evolution.genetics.washington.edu/phylip/newicktree.html). One can have either support values for internal nodes or a node label, but not both.
