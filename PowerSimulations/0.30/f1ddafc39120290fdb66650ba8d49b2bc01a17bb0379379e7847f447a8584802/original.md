Struct to create the constraint that set the flow limits through an HVDC two-terminal branch.

For more information check [Branch Formulations](@ref PowerSystems.Branch-Formulations).

The specified constraint is formulated as:

$$
R^\text{min} \le f_t \le R^\text{max}, \quad \forall t \in \{1,\dots,T\}
$$
