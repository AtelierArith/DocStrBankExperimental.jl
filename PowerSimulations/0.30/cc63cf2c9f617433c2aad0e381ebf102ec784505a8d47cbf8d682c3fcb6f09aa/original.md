Struct to create the constraint that sets the reactive power to the power factor in the RenewableConstantPowerFactor formulation for renewable units.

For more information check [RenewableGen Formulations](@ref PowerSystems.RenewableGen-Formulations).

The specified constraint is formulated as:

$$
q_t^\text{re} = \text{pf} \cdot p_t^\text{re}, \quad \forall t \in \{1,\dots, T\}
$$
