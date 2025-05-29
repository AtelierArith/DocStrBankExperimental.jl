```
mutable struct FENodeSet{T}
```

Finite element node set type.

The only field is `xyz`, as the array of node locations. Indexed with the node number. The location of node `j` is given by `xyz[j,:]`. Clearly, the nodes needs to be numbered between `1` and `size(xyz, 1)`.

!!! note
    The constructor makes a *copy* of the input `xyz` array for safety.

