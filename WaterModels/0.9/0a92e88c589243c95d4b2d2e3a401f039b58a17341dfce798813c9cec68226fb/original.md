```
objective_owf(wm::AbstractWaterModel)
```

Sets the objective for optimal water flow (owf) problem specifications. By default, minimizes the costs associated with (1) extracting water from each reservoir at some volumetric flow rate and (2) pumping operations, which consume power at predefined electricity rates. That is, the objective is

$$
\text{minimize} ~ \sum_{t \in \mathcal{T}^{\prime}} \Delta t
\left(\left[\sum_{(i, j) \in \mathcal{P}_{t}} \pi_{ijt} P_{ijt}\right] +
\left[\sum_{i \in \mathcal{R}_{t}} \mu_{it} q_{it}\right]\right),
$$

where $\mathcal{T}^{\prime} := \mathcal{T} \setminus \{T\}$ is the set of time indices without the last time index, which is reserved only for computing the final volumes of tanks; $\Delta t$ is the time step connecting time $t$ with time $t + 1$; $\mathcal{P}_{t}$ is the set of pumps available for operation at time $t$; $\pi_{ijt}$ is the price of electricity (cost per unit energy) used for pumping at pump $(i, j)$ and time $t$; $P_{ijt}$ is the power consumption of pump $(i, j)$ at time $t$; $\mathcal{R}_{t}$ is the set of reservoirs available at time $t$; $\mu_{it}$ is the cost of extracting (and treating) one volumetric unit of water from reservoir $i$ at time $t$; and $q_{it}$ is the volumetric flow rate of water extracted from reservoir $i$ at time $t$.
