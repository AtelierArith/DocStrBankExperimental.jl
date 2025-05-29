```
set_outgroup!(node::Node)
```

Set the node `node` as an outgroup to the tree to which it belongs. This will introduce a root node between `node` and its parent. When the tree has a trifurcating root, this will resolve the trifurcation (i.e. root the tree). When the tree is already bifuracting, this will reroot the tree. (perhaps it would be wise to split these two functionalities, since they do different things... i.e. rooting/rerooting).

```julia
julia> tr = nw"(A,(B,(C,D)),E);"
(A,(B,(C,D)),E);
julia> NewickTree.set_outgroup!(tr[2][1])
(((C,D),(A,E)),B);
```
