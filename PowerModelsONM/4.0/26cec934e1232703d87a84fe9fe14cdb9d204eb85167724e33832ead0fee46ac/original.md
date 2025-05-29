```
constraint_isolate_block(pm::AbstractUnbalancedPowerModel, nw::Int)
```

constraint to ensure that blocks get properly isolated by open switches by comparing the states of two neighboring blocks. If the neighboring block indicators are not either both 0 or both 1, the switch between them should be OPEN (0)

$$
\begin{align*}
& (z^{bl}_{fr} - z^{bl}_{to}) \leq  \gamma_{i}\ ~\forall i \in S \\
& (z^{bl}_{fr} - z^{bl}_{fr}) \geq - \gamma_{i}\ ~\forall i \in S \\
& z^{bl}_b \leq N_{gen} + N_{strg} + N_{neg load} + \sum_{i \in S \in b} \gamma_i, ~\forall b \in B
\end{align*}
$$

where $z^{bl}_{fr}$ and $z^{bl}_{to}$ are the indicator variables for the blocks on either side of switch $i$.
