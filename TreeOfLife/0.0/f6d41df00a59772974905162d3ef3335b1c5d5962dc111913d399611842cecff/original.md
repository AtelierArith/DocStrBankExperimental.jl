```
fromnewick(str::AbstractString; nocomments::Bool=false) :: AbstractTree
```

Create a phylogenetic tree from a Newick-format tree string.

Its inverse function is [`tonewick`](@ref).

The argument `nocomments` controls whether the comments (enclosed by square  brackets) are wiped out; by default it is set to `false`, i.e., all comments  are kept.
