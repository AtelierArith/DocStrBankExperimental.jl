Constraint for modeling a variable load (i.e., connected to a pump). Since the base power formulation uses a variable, $0 \leq z_{it} \leq 1$, to model the proportion of maximum load served at load $i \in \mathcal{L}$, time index $t \in \mathcal{T}$, a value of one indicates the maximum load is being served (denoted as $pd$). Any other value will represent some proportion of this maximum. Linking pump power to load is thus modeled via

$$
P_{jt} = z_{it} \sum_{c \in \mathcal{C}} pd_{ict}, \,
\forall (i, j) \in \mathcal{D}, \, \forall t \in \mathcal{T},
$$

where $\mathcal{D}$ is the set of interdependencies, linking loads, $i \in \mathcal{L}$, to pumps, $j \in \mathcal{P}$. Here, $P_{j}$ is a variable that represents pump power and $\mathcal{C}$ is the set of conductors, i.e., power is bounded by $\sum_{c \in \mathcal{C}} pd_{ict}$.
