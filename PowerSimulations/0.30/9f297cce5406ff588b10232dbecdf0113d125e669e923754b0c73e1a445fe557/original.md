Struct to create the constraint for satisfying active power reserve requirements. For more information check [Service Formulations](@ref service_formulations).

The constraint is as follows:

$$
\sum_{d\in\mathcal{D}_s} r_{d,t} + r_t^\text{sl} \ge \text{Req},\quad \forall t\in \{1,\dots, T\} \quad \text{(for a ConstantReserve)} \\
\sum_{d\in\mathcal{D}_s} r_{d,t} + r_t^\text{sl} \ge \text{RequirementTimeSeriesParameter}_{t},\quad \forall t\in \{1,\dots, T\} \quad \text{(for a VariableReserve)}
$$
