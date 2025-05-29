```
function get_jacobian(
::Type{T},
system::PSY.System,
sparse_retrieve_loop::Int = 3,
) where {T <: SimulationModel}
```

Returns the jacobian function of the system model resulting from the system data.

# Arguments:

  * `::SimulationModel` : Type of Simulation Model. `ResidualModel` or `MassMatrixModel`. See [Models Section](https://nrel-sienna.github.io/PowerSimulationsDynamics.jl/stable/models/) for more details
  * `system::PowerSystems.System` : System data
  * `sparse_retrieve_loop::Int` : Number of loops for sparsity detection. If 0, builds the Jacobian with a DenseMatrix
