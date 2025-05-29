Struct to create the constraint the AC branch flows depending on the network model. For more information check [Branch Formulations](@ref PowerSystems.Branch-Formulations).

The specified constraint depends on the network model chosen. The most common application is the StaticBranch in a PTDF Network Model:

$$
f_t = \sum_{i=1}^N \text{PTDF}_{i,b} \cdot \text{Bal}_{i,t}, \quad \forall t \in \{1,\dots, T\}
$$
