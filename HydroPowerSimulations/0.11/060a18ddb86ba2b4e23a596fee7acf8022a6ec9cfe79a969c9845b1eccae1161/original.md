Struct to create the constraint that limits the budget for reservoir formulations.

For more information check [HydroPowerSimulations Formulations](@ref HydroPowerSimulations-Formulations).

The specified constraint is formulated as:

$$
\sum_{t=1}^T p^\text{hy}_t \le \sum_{t=1}^T \text{EnergyBudgetTimeSeriesParameter}_t,
$$
