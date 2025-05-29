Struct to create the constraint that set the flow to-from limits through an HVDC two-terminal branch.

For more information check [Branch Formulations](@ref PowerSystems.Branch-Formulations).

The specified constraint is formulated as:

$$
R^\text{to,min} \le f_t^\text{to-from}  \le R^\text{to,max},\quad \forall t \in \{1,\dots, T\}
$$
