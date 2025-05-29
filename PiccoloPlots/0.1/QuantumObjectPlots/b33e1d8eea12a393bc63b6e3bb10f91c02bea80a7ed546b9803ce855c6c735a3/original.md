```
plot_unitary_populations(
    traj::NamedTrajectory;
    unitary_columns::AbstractVector{Int}=1:2,
    unitary_name::Symbol=:Ũ⃗,
    control_name::Symbol=:a,
    kwargs...
)
```

Plot the populations of the unitary columns of the unitary matrix in the trajectory. `kwargs` are passed to [`NamedTrajectories.plot`](https://docs.harmoniqs.co/NamedTrajectories/dev/generated/plotting/).

# Keyword Arguments

  * `unitary_columns::AbstractVector{Int}`: The columns of the unitary matrix to plot the populations of. Default is `1:2`.
  * `unitary_name::Symbol`: The name of the unitary matrix in the trajectory. Default is `:Ũ⃗`.
  * `control_name::Symbol`: The name of the control in the trajectory. Default is `:a`.
  * `kwargs...`: Additional keyword arguments passed to [`NamedTrajectories.plot`](https://docs.harmoniqs.co/NamedTrajectories/dev/generated/plotting/).
