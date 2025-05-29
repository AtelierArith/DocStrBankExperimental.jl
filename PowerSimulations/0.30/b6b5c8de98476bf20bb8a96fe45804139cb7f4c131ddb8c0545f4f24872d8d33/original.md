Struct to create the constraint for upper bound feedforward limits.

For more information check [Feedforward Formulations](@ref ff_formulations).

The specified constraint is formulated as:

$$
\begin{align*}
&  \text{AffectedVariable}_t - p_t^\text{ff,ubsl} \le \text{SourceVariableParameter}_t, \quad \forall t \in \{1,\dots, T\}
\end{align*}
$$
