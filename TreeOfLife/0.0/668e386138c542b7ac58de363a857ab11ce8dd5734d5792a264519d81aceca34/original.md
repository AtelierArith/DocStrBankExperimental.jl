```
cutfromroot(tree::ChronoTree, dist::Real; keep::Symbol=:both)
	:: Union{Vector{NTuple{2,Int}}, Vector{Int}}
```

Find the temporal section by `dist` time units after the root is born.  The argument `keep` can be set among four options, i.e., `:both` (tuples  containing parents and childs), `:parent`, `:child`, or `:closer`. 
