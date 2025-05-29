```
NewickData{T,S<:AbstractString}
```

A simple container for the allowed fields in a newick tree. Those are the `distance` (expected number of substitutions, time, what have you), `support` (e.g. bootstrap support value, posterior clade probability) and `name` (leaf names). Note that internal node labels are not allowed.
