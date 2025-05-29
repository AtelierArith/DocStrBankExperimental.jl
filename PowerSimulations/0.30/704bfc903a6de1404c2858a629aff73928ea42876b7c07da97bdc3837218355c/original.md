Struct to create the constraint to limit active power expressions by a time series parameter. For more information check [Device Formulations](@ref formulation_intro).

The specified constraint depends on the UpperBound expressions, but in its most basic formulation is of the form:

$$
p_t \le \text{ActivePowerTimeSeriesParameter}_t, \quad \forall t \in \{1,\dots,T\}
$$
