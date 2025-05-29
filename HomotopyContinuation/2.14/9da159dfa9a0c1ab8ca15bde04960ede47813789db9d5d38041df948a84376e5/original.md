```
ParameterHomotopy(F::Union{AbstractSystem,System}; start_parameters, target_parameters)
ParameterHomotopy(F::Union{AbstractSystem,System}, start_parameters, target_parameters)
```

Construct the parameter homotopy $H(x,t) = F(x; t p + (1 - t) q)$ where $p$ is `start_parameters` and $q$ is `target_parameters`.
