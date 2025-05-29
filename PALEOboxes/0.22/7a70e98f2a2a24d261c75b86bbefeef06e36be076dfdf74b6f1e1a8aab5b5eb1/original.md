```
VarList_vector(varcollection; components=false, forceview=false) -> VarList_vector
```

Create a `VarList_vector` describing a collection of `VariableReaction`s, `create_accessors` will then return a Vector of data arrays.

If `components = true`, each Vector element will be a Vector of data array components.

If `forceview = true`, each accessor will be a 1-D `view` to help type stability, even if this is redundant (ie no `view` required, v::Vector -> view(v, 1:length(v)))
