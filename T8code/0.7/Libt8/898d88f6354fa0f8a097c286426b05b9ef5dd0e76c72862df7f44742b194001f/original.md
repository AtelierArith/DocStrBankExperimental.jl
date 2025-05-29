```
t8_stash
```

The stash data structure is used to store information about the cmesh before it is committed. In particular we store the eclasses of the trees, the face-connections and the tree attributes. Using the stash structure allows us to have a very flexible interface. When constructing a new mesh, the user can specify all these mesh entities in arbitrary order. As soon as the cmesh is committed the information is copied from the stash to the cmesh in an order mannered.

| Field      | Note                                                                   |
|:---------- |:---------------------------------------------------------------------- |
| classes    | Stores the eclasses of the trees.  # See also [`t8_stash_class`](@ref) |
| joinfaces  | Stores the face-connections.  # See also [`t8_stash_joinface`](@ref)   |
| attributes | Stores the attributes.  # See also [`t8_stash_attribute`](@ref)        |
