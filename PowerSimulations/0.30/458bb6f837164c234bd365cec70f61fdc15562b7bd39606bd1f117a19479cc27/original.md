Struct to create the constraint that set the flow from-to limits through an HVDC two-terminal branch.

For more information check [Branch Formulations](@ref PowerSystems.Branch-Formulations).

The specified constraint is formulated as:

$$
R^\text{from,min} \le f_t^\text{from-to}  \le R^\text{from,max}, \forall t \in \{1,\dots, T\}
$$
