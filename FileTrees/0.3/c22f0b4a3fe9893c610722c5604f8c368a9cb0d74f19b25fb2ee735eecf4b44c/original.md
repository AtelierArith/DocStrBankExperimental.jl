```
mapsubtrees(f, t::FileTree, pattern::Union{GlobMatch, Regex})
```

For every node that matches the pattern provided, apply the function `f`.

If `f` returns either a `File` or `FileTree`, this new node will replace the matched node.

If `f` returns `nothing`, the matched node will be deleted

If `f` returns any other value, the value will be used as the value of the node and the node itself will be emptied of children.

This will allow use of mapsubtrees for complex use cases.

Suppose you would like to combine the values of a subdirectory with the function `hcat` and in turn those values using `vcat`, you can use `mapsubtrees` to accomplish this:

Here is a demo:

```julia
t = maketree("dir"=>([string(j)=>[(name=string(i), value=(i,j)]
                        for i=1:2] for j=1:3]

t1 = mapsubtrees("*") do subtree
    reducevalues(vcat, subtree)
end
```

```julia
reducevalues(hcat, t1)
```
