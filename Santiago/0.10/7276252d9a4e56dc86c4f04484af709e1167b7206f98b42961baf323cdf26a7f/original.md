```julia
massflow(
    sys::Santiago.System,
    M_in::Dict{String, Dict{String, T<:Real}};
    MC,
    scale_reliability,
    rng
) -> Dict{Santiago.Tech, NamedArrays.NamedArray{Float64}}

```

Compute massflows of a system. Optionally with Monte Carlo (MC) simulation.

## Arguments:

  * `M_in`: a dictionary containing for each source the inflows of each substance.
  * `MC`: if false, the expected values of the Dirichlet distribution is used as transfer.  coefficients. Else, the transfer coefficients are sampled from a Dirichlet distribution.
  * `scale_reliability`: factor to scale the `transC_reliability` of all `Techs`.
  * `rng`: optional, a random generator. This is only needed for multi-threading to obtain thread-safety.
