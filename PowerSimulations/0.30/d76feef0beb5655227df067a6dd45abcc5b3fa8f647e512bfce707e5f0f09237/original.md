Struct to create the constraint to balance power across specified areas. For more information check [Network Formulations](@ref network_formulations).

The specified constraint is generally formulated as:

$$
\sum_{c \in \text{components}_a} p_t^c = 0, \quad \forall a\in \{1,\dots, A\}, t \in \{1, \dots, T\}
$$
