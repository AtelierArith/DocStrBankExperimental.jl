Struct to create the constraint for lower bound feedforward limits.

For more information check [Feedforward Formulations](@ref ff_formulations).

The specified constraint is formulated as:

$$
\begin{align*}
&  \text{AffectedVariable}_t + p_t^\text{ff,lbsl} \ge \text{SourceVariableParameter}_t, \quad \forall t \in \{1,\dots, T\}
\end{align*}
$$
