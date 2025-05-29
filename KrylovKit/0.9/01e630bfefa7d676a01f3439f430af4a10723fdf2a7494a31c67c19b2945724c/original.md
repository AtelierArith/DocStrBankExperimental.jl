```
EigSorter(by; rev = false)
```

A simple `struct` to be used in combination with [`eigsolve`](@ref) or [`schursolve`](@ref) to indicate which eigenvalues need to be targeted, namely those that appear first when sorted by `by` and possibly in reverse order if `rev == true`.
