Struct to create the constraints that set the power balance across a lossy HVDC two-terminal line.

For more information check [Branch Formulations](@ref PowerSystems.Branch-Formulations).

The specified constraints are formulated as:

$$
\begin{align*}
& f_t^\text{to-from} - f_t^\text{from-to} \le L_1 \cdot f_t^\text{to-from} - L_0,\quad \forall t \in \{1,\dots, T\} \\
& f_t^\text{from-to} - f_t^\text{to-from} \ge L_1 \cdot f_t^\text{from-to} + L_0,\quad \forall t \in \{1,\dots, T\} \\
& f_t^\text{from-to} - f_t^\text{to-from} \ge - M^\text{big} (1 - u^\text{dir}_t),\quad \forall t \in \{1,\dots, T\} \\
& f_t^\text{to-from} - f_t^\text{from-to} \ge - M^\text{big} u^\text{dir}_t,\quad \forall t \in \{1,\dots, T\} \\
\end{align*}
$$
