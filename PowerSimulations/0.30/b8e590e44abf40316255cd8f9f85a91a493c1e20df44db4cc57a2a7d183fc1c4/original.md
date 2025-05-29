Struct to create the constraint for ensuring that NonSpinning Reserve can be delivered from turn-off thermal units.

For more information check [Service Formulations](@ref service_formulations) for NonSpinningReserve.

The constraint is as follows:

$$
r_{d,t} \le (1 - u_{d,t}^\text{th}) \cdot R^\text{limit}_d, \quad \forall d \in \mathcal{D}_s, \forall t \in \{1,\dots, T\}
$$
