Struct to create the constraint that set the angle limits through a PhaseShiftingTransformer.

For more information check [Branch Formulations](@ref PowerSystems.Branch-Formulations).

The specified constraint is formulated as:

$$
\Theta^\text{min} \le \theta^\text{shift}_t \le \Theta^\text{max}, \quad \forall t \in \{1,\dots,T\}
$$
