Constraint for modeling a fixed load (i.e., not connected to a pump). Since the base power formulation uses a variable, $0 \leq z_{it} \leq 1$, to model the proportion of maximum load served at load $i \in \mathcal{L}$, time index $t \in \mathcal{T}$, a value of one indicates the full load being served, as expected for non-pump loads. That is, these constraints are

$$
z_{it} = 1, \, \forall i \in \mathcal{L}^{\prime},
\, \forall t \in \mathcal{T},
$$

where $\mathcal{L}^{\prime}$ is the set of loads not connected to a pump.
