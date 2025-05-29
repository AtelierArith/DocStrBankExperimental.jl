```
IsothermData(; 
    partial_pressures_mpa=nothing, concentrations_cc=nothing, activities=nothing, temperature_k=nothing, 
    rho_pol_g_cm3=nothing, pen_mws_g_mol=nothing,
)
```

Container for all data relevant to isotherms.

Data specific to each component and step are organized in matrix format with columns representing components and rows representing steps i.e., with s -> step and c -> component:

```
    [ s1c1  s1c2  s1c3 ...
      s2c1  s2c2  s2c3 ...
      s3c1  s3c2  s3c3 ...
      ...   ...   ...  ... ]
```

# Inputs

Inputs can be vectors of vectors e.g., `partial_pressures_mpa = [[component_1-step_1, component_1-step_2, ...], [component_2-step_1, component_2-step_2, ...], ...]` Or, if only one component is present, only a vector e.g., `[step_1, step_2, ...]`
