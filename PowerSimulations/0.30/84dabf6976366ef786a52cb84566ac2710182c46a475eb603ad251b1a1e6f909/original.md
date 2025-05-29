Struct to create the constraint to limit active power input expressions. For more information check [Device Formulations](@ref formulation_intro).

The specified constraint depends on the UpperBound and LowerBound expressions, but in its most basic formulation is of the form:

$$
P^\text{min} \le p_t^\text{in} \le P^\text{max}, \quad \forall t \in \{1,\dots,T\}
$$
