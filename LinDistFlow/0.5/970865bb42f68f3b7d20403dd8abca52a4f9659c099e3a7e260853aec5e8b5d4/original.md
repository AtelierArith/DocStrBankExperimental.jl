```
constrain_line_amps(m::JuMP.AbstractModel, p::Inputs{MultiPhase})
```

Constrain the estimated line amps using the `p.Isquared_up_bounds` in both the postive and negative directions.

See `define_line_amps_pu` for more.
