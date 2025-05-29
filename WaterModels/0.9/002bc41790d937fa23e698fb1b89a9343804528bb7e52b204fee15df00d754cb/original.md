```
variable_pump_power(
    wm::AbstractWaterModel;
    nw::Int=nw_id_default,
    bounded::Bool=true,
    report::Bool=true
)
```

Creates bounded (by default) or unbounded power consumption variables for pumps in the network at subnetwork (or time) index `nw`, i.e., `P[a]` for `a` in `pump`. Note that these variables are always nonnegative since each pump only *consumes* power. Additionally, two sets of JuMP expressions are also derived from these power variables: energy consumption, i.e., `E[a]` for `a` in `pump` and cost of pump operation across a time step, i.e., `c[a]` for `a` in `pump`.
