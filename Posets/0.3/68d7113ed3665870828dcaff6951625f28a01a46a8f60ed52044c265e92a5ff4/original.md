```
dual_ranking(p::Poset, compact::Bool = true)::Dict{Int,Int}
```

A variant on `ranking` from `Posets` by combining `ranking` on both `p`  and its dual. 

With `compact` set to `true` the levels are "collapsed" to be numbered 0, 1, 2, 3, etc. Otherwise, there may be gaps in the numbering and might not start at 0.
