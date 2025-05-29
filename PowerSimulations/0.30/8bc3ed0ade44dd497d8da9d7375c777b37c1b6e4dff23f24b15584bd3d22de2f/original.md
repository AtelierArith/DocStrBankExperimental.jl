Struct to create the commitment constraint between the on, start, and stop variables. For more information check [ThermalGen Formulations](@ref ThermalGen-Formulations).

The specified constraints are formulated as:

$$
u_1^\text{th} = u^\text{th,init} + v_1^\text{th} - w_1^\text{th} \\
u_t^\text{th} = u_{t-1}^\text{th} + v_t^\text{th} - w_t^\text{th}, \quad \forall t \in \{2,\dots,T\} \\
v_t^\text{th} + w_t^\text{th} \le 1, \quad \forall t \in \{1,\dots,T\}
$$
