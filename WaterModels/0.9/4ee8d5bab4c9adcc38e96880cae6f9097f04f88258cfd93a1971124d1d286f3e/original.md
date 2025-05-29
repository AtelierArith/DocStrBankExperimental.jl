```
objective_des(wm::AbstractWaterModel)
```

Sets and returns the objective function for network design (des) problem specifications. By default, the cost of selecting the discrete pipe resistances over all design pipes and time indices is minimized. That is, the objective is

$$
\text{minimize} ~ \sum_{t \in \mathcal{T}}
\sum_{(i, j) \in \mathcal{A}^{\textrm{des}}_{t}} c_{ijt} z_{ijt},
$$

where $\mathcal{T}$ is the set of time indices, $\mathcal{A}^{\textrm{des}}_{t}$ is the set of design pipes that are available at time index $t$, $c_{ijt}$ is the cost of installing design pipe $(i, j)$ at time index $t$, and $z_{ijt}$ is a binary variable indicating whether (1) or not (0) the design pipe is selected for construction.
