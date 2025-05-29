Struct to create the constraint to participation assignments limits in the active power reserves. For more information check [Service Formulations](@ref service_formulations).

The constraint is as follows:

$$
r_{d,t} \le \text{Req} \cdot \text{PF} ,\quad \forall d\in \mathcal{D}_s, \forall t\in \{1,\dots, T\} \quad \text{(for a ConstantReserve)} \\
r_{d,t} \le \text{RequirementTimeSeriesParameter}_{t} \cdot \text{PF}\quad  \forall d\in \mathcal{D}_s, \forall t\in \{1,\dots, T\}, \quad \text{(for a VariableReserve)}
$$
