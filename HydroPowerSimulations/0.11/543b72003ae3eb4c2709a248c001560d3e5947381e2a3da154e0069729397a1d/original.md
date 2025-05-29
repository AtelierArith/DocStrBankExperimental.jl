Struct to create the constraint that keeps track of the reservoir level of the lower (down) reservoir

For more information check [HydroPowerSimulations Formulations](@ref HydroPowerSimulations-Formulations).

The specified constraint is formulated as:

$$
e_{t}^\text{dn} = e_{t-1}^\text{dn} + \left (p_t^\text{hy,out} + s_t - \frac{p_t^\text{hy,in}}{\eta^\text{pump}} \right) \Delta T - \text{OutflowTimeSeriesParameter}_t, \quad \forall t \in \{1,\dots, T\}
$$
