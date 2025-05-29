```
newnode, newdepth = prev(node, depth::Int=0)
```

Return the previous node in a depth-first search. `depth` counts the number of levels below the root.

This traverses in the opposite direction as [`next`](@ref), so last, deepest children are visited before their parents.
