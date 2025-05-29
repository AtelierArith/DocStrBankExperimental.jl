```
writenw(io::IO, n)
writenw(fname::AbstractString, n)
```

Write a newick representation of the tree rooted in `n`. Note that the tree data type should allow `nwstr(n)` to work. See the `nwstr` docstring.
