```
build_bim_polar!(m::JuMP.AbstractModel, net::Network{SinglePhase}, ::Val{Unrelaxed})
```

Model builder for single-phase, unrelaxed BIM with polar voltage variables. See the      [Single Phase Bus Injection Model (Unrelaxed)](@ref) math for details.

Adds the variables:

  * `m[:v_mag]` for all busses in `CommonOPF.busses(net)`
  * `m[:v_ang]` for all busses in `CommonOPF.busses(net)`
  * `m[:p0]` and `m[:q0]` for the slack bus power injection
  * `m[:q_gen]` for any P-V busses (via the `CommonOPF.Generator`)
