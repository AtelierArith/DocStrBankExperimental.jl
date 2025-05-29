Struct to create the constraint that set-up the target for reservoir formulations.

For more information check [HydroPowerSimulations Formulations](@ref HydroPowerSimulations-Formulations).

The specified constraint is formulated as:

$$
e_t + e^\text{shortage} + e^\text{surplus} = \text{EnergyTargetTimeSeriesParameter}_t, \quad \forall t \in \{1,\dots, T\}
$$
