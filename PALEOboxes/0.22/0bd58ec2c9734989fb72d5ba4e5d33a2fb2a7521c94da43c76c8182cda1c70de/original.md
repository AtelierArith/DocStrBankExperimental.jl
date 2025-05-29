```
VarList_tuple(varcollection; components=false) -> VarList_tuple
```

Create a `VarList_tuple` describing a collection of `VariableReaction`s, `create_accessors` will then return a Tuple of data arrays.

An entry of `nothing` in `varcollection` will produce `nothing` in the corresponding entry in the Tuple of arrays supplied to the Reaction method.

If `components = true`, each Tuple field will be a Vector of data array components.
