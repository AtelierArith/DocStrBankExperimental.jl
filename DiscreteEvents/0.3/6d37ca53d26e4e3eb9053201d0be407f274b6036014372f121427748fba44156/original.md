```
Clock(Δt::T=0.01; t0::U=0, unit::FreeUnits=NoUnits) where {T<:Number,U<:Number}
```

Create a new virtual clock.

# Arguments

  * `Δt::T=0.01`: time increment for sampling. Δt can be set later with `sample_time!`.
  * `t0::U=0`: start time for simulation
  * `unit::FreeUnits=NoUnits`: clock time unit. Units can be set explicitely by   setting e.g. `unit=minute` or implicitly by giving Δt as a time or else setting   t0 to a time, e.g. `t0=60s`.

The created clock has id==1 (master).
