Struct to create the RampConstraint associated with a specified thermal device or reserve service.

For thermal units, see more information in [Thermal Formulations](@ref ThermalGen-Formulations). The constraint is as follows:

$$
-R^\text{th,dn} \le p_t^\text{th} - p_{t-1}^\text{th} \le R^\text{th,up}, \quad \forall  t\in \{1, \dots, T\}
$$

For Ramp Reserve, see more information in [Service Formulations](@ref service_formulations). The constraint is as follows:

$$
r_{d,t} \le R^\text{th,up} \cdot \text{TF}\quad  \forall d\in \mathcal{D}_s, \forall t\in \{1,\dots, T\}, \quad \text{(for ReserveUp)} \\
r_{d,t} \le R^\text{th,dn} \cdot \text{TF}\quad  \forall d\in \mathcal{D}_s, \forall t\in \{1,\dots, T\}, \quad \text{(for ReserveDown)}
$$
