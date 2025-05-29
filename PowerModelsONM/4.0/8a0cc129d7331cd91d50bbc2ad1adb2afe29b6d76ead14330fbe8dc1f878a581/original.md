```
constraint_mc_switch_open_voltage_distance(pm::PMD.AbstractUnbalancedRectangularModels, nw::Int, i::Int, f_bus::Int, t_bus::Int, f_connections::Vector{Int}, t_connections::Vector{Int}, vm_delta_pu::Real, ::Real)
```

Constraints for voltages on either side of an open switch to be within some distance of one another (provided by user) for Rectangular models math``` \begin{align}     \sqrt{\Re{V*{i,\phi}}^2 + \Im{V*{i,\phi}}^2}-\sqrt{\Re{V*{j,\phi}}^2 + \Im{V*{j,\phi}}^2} &\leq \overline{\delta}^{|V|}*{k} + \tau^{|V|}*{k,\phi},   \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \
    -\left[\sqrt{\Re{V*{i,\phi}}^2 + \Im{V*{i,\phi}}^2}-\sqrt{\Re{V*{j,\phi}}^2 + \Im{V*{j,\phi}}^2}\right] &\leq \overline{\delta}^{|V|}*{k} + \tau^{|V|}*{k,\phi},   \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \
    \arctan{\left(\frac{\Im{V*{i,\phi}}}{\Re{V*{i,\phi}}}\right)}-\arctan{\left(\frac{\Im{V*{j,\phi}}}{\Re{V*{j,\phi}}}\right)} &\leq \overline{\delta}^{\angle V}*{k} + \tau^{\angle V}*{k,\phi},   \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \
    -\left[\arctan{\left(\frac{\Im{V*{i,\phi}}}{\Re{V*{i,\phi}}}\right)}-\arctan{\left(\frac{\Im{V*{j,\phi}}}{\Re{V*{j,\phi}}}\right)}\right] &\leq \overline{\delta}^{\angle V}*{k} + \tau^{\angle V}*{k,\phi},   \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \end{align}

```

math```
\begin{align}
        \tau^{V}_{k,\phi} = \left(\frac{\tau^{|V|}_{k,\phi}}{\overline{\delta}^{|V|}_{k,\phi}}\right)^2 +\left(\frac{\tau^{\angle V}_{k,\phi}}{\overline{\delta}^{\angle V}_{k,\phi}}\right)^2, \; \; \forall (i,j,k) \in {\cal E}_{sw}^{\mathrm{open}},\forall \phi \in \Phi
\end{align}

```
