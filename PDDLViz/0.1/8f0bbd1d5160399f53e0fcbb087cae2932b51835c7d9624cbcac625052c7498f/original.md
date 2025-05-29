```
Controller
```

Abstract supertype for all controllers. When attached to a canvas, a controller interprets user input as PDDL actions and updates the canvas accordingly.

Can be attached to a canvas using [`add_controller!`](@ref), and removed using [`remove_controller`](@ref).
