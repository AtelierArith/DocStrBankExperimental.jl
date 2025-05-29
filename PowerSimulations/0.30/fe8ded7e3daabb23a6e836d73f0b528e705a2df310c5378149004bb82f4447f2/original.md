Struct to create the constraint for semicontinuous feedforward limits.

For more information check [Feedforward Formulations](@ref ff_formulations).

The specified constraint is formulated as:

$$
\begin{align*}
&  \text{ActivePowerRangeExpressionUB}_t := p_t^\text{th} - \text{on}_t^\text{th}P^\text{th,max} \le 0, \quad  \forall t\in \{1, \dots, T\}  \\
&  \text{ActivePowerRangeExpressionLB}_t := p_t^\text{th} - \text{on}_t^\text{th}P^\text{th,min} \ge 0, \quad  \forall t\in \{1, \dots, T\}
\end{align*}
$$
