```
writesubtree!(IO, node, edge, dendroscope::Bool, namelabel::Bool,
              round_branch_lengths::Bool, digits::Integer, internallabel::Bool)
```

Write the extended newick format of the sub-network rooted at `node` and assuming that `edge` is a parent of `node`.

If the parent `edge` is `nothing`, the edge attribute `ischild1` is used and assumed to be correct to write the subtree rooted at `node`. This is useful to write a subtree starting at a non-root node. Example:

```julia
net = readnewick("(((A,(B)#H1:::0.9),(C,#H1:::0.1)),D);")
directedges!(net)
s = IOBuffer()
writesubtree!(s, net.node[7], nothing, false, true)
String(take!(s))
```

Used by [`writenewick`](@ref).
