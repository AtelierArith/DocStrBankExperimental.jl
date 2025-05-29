```
FlowConnector(state; n_in, n_out, name)
```

A component for connecting multiple flows.

This system takes an arbitrary number of inputs and splits it into a number of outputs.  Thereby, it is ensuring mass conservation and assumes ideal mixing between the incoming flows such that the concentrations in all outflows are equal. The flow rates of the outflows are to be  provided by the following systems, e.g. using a [`FlowPump`](@ref) system. The flow rates have to be provided for all except one outflow, the last one is determined from a mass balance.

Specifically, it has the following equations ($C$ always stands for an arbitrary component):

  * Conservation of mass:

$$
\begin{aligned}
\sum_{i = 0}^{n_{in}}q_{in,i} &= \sum_{i=0}^{n_{out}}q_{out,i}\\
\sum_{i = 0}^{n_{in}}C_{in,i}q_{in,i} &= \sum_{i=0}^{n_{out}}C_{out,i}q_{out,i}
\end{aligned}
$$

  * Ideal mixing:

$$
C_{out,i} = C_{out,j} \quad \forall i,j\in \{1 ... n_{out}\}
$$

# Parameters:

  * `states`: The components in the flows
  * `n_in`: The number of inflows
  * `n_out`: The number of outflows

# Connectors:

  * `inflow_i`: The i-th inflow of the `FlowConnector` (if only one inflow, the `_i` is omitted and the resulting name is `inflow`)
  * `outflow_i`: The i-th outflow of the `FlowConnector` (if only one inflow, the `_i` is omitted and the resulting name is `outflow`)
