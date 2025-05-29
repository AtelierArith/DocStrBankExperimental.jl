```
AssemblyState{TF, TP<:AbstractVector{PointState{TF}}, TE<:AbstractVector{ElementState{TF}}}
```

Struct for storing state variables for the points and elements in an assembly.

# Fields:

  * `points::TP`: Array of [`PointState`](@ref) for each point in the assembly
  * `elements::TE`: Array of [`ElementState`](@ref) for each element in the assembly
