```
foldup(node::DAG, 
    f_leaf::Function, 
    f_inner::Function, 
    ::Type{T})::T where {T}
```

Compute a function bottom-up on the graph.  `f_leaf` is called on leaf nodes, and `f_inner` is called on inner nodes. Values of type `T` are passed up the circuit and given to `f_inner` as a function on the children.
