```
add_component!(traj, name::Symbol, data::AbstractVecOrMat; type={:state, :control, :slack})
```

Add a component to the trajectory.

This function resizes the trajectory, so global components and components must be adjusted.
