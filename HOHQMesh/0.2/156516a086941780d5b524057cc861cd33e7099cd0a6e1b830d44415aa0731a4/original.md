```
addOuterBoundary!(proj::Project, outerBoundary::Dict{String,Any})
```

Add an empty outer boundary to the project. There can be only one. This function is only used as part of an undo operation removing the outer boundary.
