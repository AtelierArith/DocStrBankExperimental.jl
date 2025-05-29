```
build_mpc!(m::JuMP.AbstractModel, p::MPCInputs)
```

Add variables and constraints for model predictive control model.  Similar to a REopt model but with any length of horizon (instead of one calendar year, and the DER sizes must be provided.
