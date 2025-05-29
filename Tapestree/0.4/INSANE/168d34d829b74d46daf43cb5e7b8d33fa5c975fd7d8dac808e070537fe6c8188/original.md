```
reorder!(tree::T, treeda::D) where {T <: iTree, D <: iTree}
```

Reorder order of daughter branches for both trees, following tree first, according to number of tips, with daughter1 always having more than daughter 2.
