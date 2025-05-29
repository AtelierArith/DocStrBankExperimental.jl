```julia
massflow_summary!(
    s::Santiago.System,
    args...;
    kwargs...
) -> Dict{String, Any}

```

Performs Monte Carlo massflow calculations and add the summary statistics to the system properties.

## Arguments:

  * `M_in`: a dictionary containing for each source the inflows of each substance.
  * `MC`: if false, the expected values of the Dirichlet distribution is used as transfer  coefficients. Else, the transfer coefficients are sampled from a Dirichlet distribution.

## Keyword arguments

  * `n`: number of Monte Carlo simulations. Ignored if `MC=false`.
  * `techflows`: if true, the flows of the individual techs are summarized.
  * `scale_reliability`: factor to scale the `transC_reliability` of all `Techs`.
  * `rng`: optional, a random generator. This is only needed for multi-threading to obtain thread-safety.
