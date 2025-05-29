Struct to create the constraint for starting up ThermalMultiStart units. For more information check [ThermalGen Formulations](@ref ThermalGen-Formulations) for ThermalMultiStartUnitCommitment.

The specified constraint is formulated as:

$$
\max\{P^\text{th,max} - P^\text{th,shdown}, 0\} \cdot w_1^\text{th} \le u^\text{th,init} (P^\text{th,max} - P^\text{th,min}) - P^\text{th,init}
$$
