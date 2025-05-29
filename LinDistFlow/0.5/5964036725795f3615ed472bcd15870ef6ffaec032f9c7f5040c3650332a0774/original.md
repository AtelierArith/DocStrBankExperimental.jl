```
define_line_amps_pu(m::JuMP.AbstractModel, p::Inputs{MultiPhase})
```

Estimating the line amps as $|(V_i - V_j) / Z|$ where we use the approximation:

$|V_i - V_j| \approx r_{ij} P_{ij} + x_{ij} Q_{ij}$

The expressions are stored in the `model.obj_dict` with key `:amps_pu`.
