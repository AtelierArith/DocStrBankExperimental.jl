```
VarList_vvector(Vector{Vector{VariableReaction}}::vars; components=false) -> VarList_vvector
```

Create a `VarList_vvector` describing a Vector of Vectors of `VariableReaction`s, `create_accessors` will then return a Vector of Vectors of data arrays.

If `components = true`, each Vector of Vectors element will be a Vector of data array components.
