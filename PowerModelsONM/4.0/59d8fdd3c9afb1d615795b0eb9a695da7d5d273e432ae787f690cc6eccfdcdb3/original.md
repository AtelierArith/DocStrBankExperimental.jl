```
constraint_mc_inverter_theta_ref(pm::PMD.AbstractUnbalancedACRModel, nw::Int, i::Int, va_ref::Vector{<:Real})
```

Creates phase angle constraints at reference buses for the ACR formulation

math`\begin{align} \Im(V) = \tan(V_a^{ref}) \Re(V) \end{align}`
