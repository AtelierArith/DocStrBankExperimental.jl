```
build_bim_rectangular!(m::JuMP.AbstractModel, net::Network{SinglePhase}, ::Val{Unrelaxed})
```

Model builder for single-phase, unrelaxed BIM with rectangular voltage variables. See the      [Single Phase Bus Injection Model (Unrelaxed)](@ref) math for details.

Adds the variables:

  * `m[:v]` with complex values for all busses in `CommonOPF.busses(net)`
  * `m[:s0]` for the complex slack bus power injection
