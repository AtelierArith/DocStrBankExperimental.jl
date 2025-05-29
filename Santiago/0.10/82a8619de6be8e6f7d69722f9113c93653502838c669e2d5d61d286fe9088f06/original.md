```julia
massflow_summary(
    sys::Santiago.System,
    M_in::Dict;
    MC,
    n,
    techflows,
    scale_reliability,
    rng
) -> Dict{String, Any}

```

Performs Monte Carlo massflow calculations and provides the summary statistics of a the main results.

## Arguments:

  * `M_in`: a dictionary containing for each source the inflows of each substance.
  * `MC`: if false, the expected values of the Dirichlet distribution is used as transfer  coefficients. Else, the transfer coefficients are sampled from a Dirichlet distribution.
  * `n`: number of Monte Carlo simulations. Ignored if `MC=false`.
  * `scale_reliability`: factor to scale the `transC_reliability` of all `Techs`.
  * `techflows`: if true, the flows of the individual techs are summarized
  * `rng`: optional, a random generator. This is only needed for multi-threading to obtain thread-safety.
