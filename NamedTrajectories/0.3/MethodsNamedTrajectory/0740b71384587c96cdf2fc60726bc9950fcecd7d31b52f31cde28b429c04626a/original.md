```
update_bound!(traj, name::Symbol, data::Real)
update_bound!(traj, name::Symbol, data::AbstractVector{<:Real})
update_bound!(traj, name::Symbol, data::Tuple{R, R} where R <: Real)
```

Update the bound of a component of the trajectory.
