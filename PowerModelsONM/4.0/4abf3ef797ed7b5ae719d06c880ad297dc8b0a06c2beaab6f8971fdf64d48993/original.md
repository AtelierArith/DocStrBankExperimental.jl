```
constraint_isolate_block_traditional(pm::AbstractUnbalancedPowerModel, nw::Int)
```

Constraint to simulate block isolation constraint in the traditional mld problem

$$
\begin{align}
& z^{bus}_{fr} - z^{bus}_{to} \leq  (1-\gamma_i), ~\forall i \in S \\
& z^{bus}_{fr} - z^{bus}_{to} \geq -(1-\gamma_i), ~\forall i \in S \\
& z^{d}_i \leq z^{d}_j, ~\forall (i,j) \in D \in B \\
& z^{d}_i \leq z^{bus}_j, ~\forall i \in D \in B, ~i \in j \in V \in B \\
& z^{bus}_i \leq z^{bus}_j, ~\forall (i,j) \in V \in B \\
& z^{bl}_b \leq N_{gen} + N_{strg} + N_{neg load} + \sum_{i \in S \in {b \in B}} \gamma_i, ~\forall b \in B
\end{align}
$$
