Struct to create the constraint that keeps track of the reservoir level of the upper (up) reservoir

For more information check [HydroPowerSimulations Formulations](@ref HydroPowerSimulations-Formulations).

The specified constraint is formulated as:

$$
e_{t}^\text{up} = e_{t-1}^\text{up} + \left (p_t^\text{hy,in} - \frac{p_t^\text{hy,out} + s_t}{\eta^\text{pump}} \right) \Delta T + \text{InflowTimeSeriesParameter}_t, \quad \forall t \in \{1,\dots, T\}
$$
