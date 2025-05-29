```
ranking(p::Poset)::Dict{Int,Int}
```

Create a ranking of the poset `p`. This is a dictionary that  gives a ranking for each element of `p`. Minimals have rank 0. Elements that are over only minimals have grade 1. And so forth. 
