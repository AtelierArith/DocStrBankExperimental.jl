Struct to create the constraint to limit reactive power expressions. For more information check [Device Formulations](@ref formulation_intro).

The specified constraint depends on the UpperBound and LowerBound expressions, but in its most basic formulation is of the form:

$$
Q^\text{min} \le q_t \le Q^\text{max}, \quad \forall t \in \{1,\dots,T\}
$$
