```
constraint_mc_switch_open_voltage_distance(pm::PMD.AbstractUnbalancedWModels, nw::Int, i::Int, f_bus::Int, t_bus::Int, f_connections::Vector{Int}, t_connections::Vector{Int}, vm_delta_pu::Real, ::Real)
```

Constraints for voltages on either side of an open switch to be within some distance of one another (provided by user) for W models

math``` \begin{align}     w*{i,\phi} - w*{j,\phi} &\leq \left(\overline{\delta}^{|V|}*{k}\right)^2 + \tau^{w}*{k,\phi}, \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \
    -\left[w*{i,\phi} - w*{j,\phi}\right] &\leq \left(\overline{\delta}^{|V|}*{k}\right)^2 + \tau^{w}*{k,\phi}, \; \; &\forall (i,j,k) \in {\cal E}*{sw}^{\mathrm{open}},\forall \phi \in \Phi \end{align}

```

math```
\begin{align}
        \tau^{V}_{k,\phi} = \frac{\upsilon^{w}_{k,\phi}}{\left(\overline{\delta}^{|V|}_{k}\right)^2}, \; \; \forall (i,j,k) \in {\cal E}_{sw}^{\mathrm{open}},\forall \phi \in \Phi
\end{align}
```

where

math``` \begin{align}     \upsilon^{w}*{k,\phi} \geq 2 (\underline{\tau}^{|V|}*{k})^2 \tau^{w}*{k,\phi} - (\underline{\tau}^{|V|}*{k})^4 \
    \upsilon^{w}*{k,\phi} \geq 2 (\overline{\tau}^{|V|}*{k})^2 \tau^{w}*{k,\phi} - (\overline{\tau}^{|V|}*{k})^4 \
    \upsilon^{w}*{k,\phi} \leq \left((\overline{\tau}^{|V|}*{k})^2 + (\underline{\tau}^{|V|}*{k})^2\right) \tau^{w}*{k,\phi} - (\overline{\tau}^{|V|}*{k})^2(\underline{\tau}^{|V|}*{k})^2 \
\end{align} ```
