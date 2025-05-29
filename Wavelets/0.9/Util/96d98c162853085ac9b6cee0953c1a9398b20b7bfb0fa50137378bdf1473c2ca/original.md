```
maketree(x::Vector, s::Symbol=:full)
maketree(n::Int, L::Int, s::Symbol=:full)
```

return a tree (BitVector) s=:full, all nodes for first L levels equal 1, others 0 s=:dwt, nodes corresponding to a dwt for first L levels equal 1, others 0
