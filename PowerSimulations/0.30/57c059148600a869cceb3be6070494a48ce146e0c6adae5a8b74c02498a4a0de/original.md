Struct to create the constraint that set the AC flow limits through branches.

For more information check [Branch Formulations](@ref PowerSystems.Branch-Formulations).

The specified constraint is formulated as:

$$
\begin{align*}
&  f_t - f_t^\text{sl,up} \le R^\text{max},\quad \forall t \in \{1,\dots, T\} \\
&  f_t + f_t^\text{sl,lo} \ge -R^\text{max},\quad \forall t \in \{1,\dots, T\}
\end{align*}
$$
