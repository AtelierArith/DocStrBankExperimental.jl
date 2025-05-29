```
constraint_mc_switch_open_voltage_distance(pm::PMD.AbstractUnbalancedPolarModels, nw::Int, i::Int, f_bus::Int, t_bus::Int, f_connections::Vector{Int}, t_connections::Vector{Int}, vm_delta_pu::Real, ::Real)
```

Constraints for voltages on either side of an open switch to be within some distance of one another (provided by user) for Polar models math``` \begin{align}     |V*{i,\phi}|-|V*{j,\phi}| &\leq \overline{\delta}^{|V|}*{k} + \tau^{|V|}*{k,\phi},   \; \; & \forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \
    -\left[|V*{i,\phi}|-|V*{j,\phi}|\right] &\leq \overline{\delta}^{|V|}*{k} + \tau^{|V|}*{k,\phi},   \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \
    \angle V*{i,\phi}-\angle V*{j,\phi} &\leq \overline{\delta}^{\angle V}*{k} + \tau^{\angle V}*{k,\phi},   \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \
    -\left[\angle V*{i,\phi}-\angle V*{j,\phi}\right] &\leq \overline{\delta}^{\angle V}*{k} + \tau^{\angle V}*{k,\phi},   \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \end{align}

```

math```
\begin{align}
        \tau^{V}_{k,\phi} = \left(\frac{\tau^{|V|}_{k,\phi}}{\overline{\delta}^{|V|}_{k,\phi}}\right)^2 +\left(\frac{\tau^{\angle V}_{k,\phi}}{\overline{\delta}^{\angle V}_{k,\phi}}\right)^2, \; \; \forall (i,j,k) \in {\cal E}_{sw}^{\mathrm{open}},\forall \phi \in \Phi
\end{align}
```
