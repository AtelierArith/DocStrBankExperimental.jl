```
build_tree(make_node::Function, ::Type{StackEntry}, stream::ParseStream; kws...)
```

Construct a tree from a ParseStream using depth-first traversal. `make_node` must have the signature

```
make_node(head::SyntaxHead, span::Integer, children)
```

where `children` is either `nothing` for leaf nodes or an iterable of the children of type `StackEntry` for internal nodes. `StackEntry` may be a node type, but also may include other information required during building the tree.

If the ParseStream has multiple nodes at the top level, `K"wrapper"` is used to wrap them in a single node.

The tree here is constructed depth-first in postorder.
