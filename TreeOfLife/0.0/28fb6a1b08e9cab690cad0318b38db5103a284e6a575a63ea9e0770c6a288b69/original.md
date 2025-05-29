```
cutfromtips(tree::ChronoTree, dist::Real; 
	keep::Symbol=:both, average=minimum, reltol=1e-6) 
	:: Union{Vector{NTuple{2,Int}}, Vector{Int}}
```

Find the temporal section by `dist` time units before the root is born. The argument `keep` can be set among four options, i.e., `:both` (tuples  containing parents and childs), `:parent`, `:child`, or `:closer`. 
