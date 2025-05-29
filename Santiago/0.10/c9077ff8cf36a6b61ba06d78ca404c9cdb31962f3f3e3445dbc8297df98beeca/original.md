```julia
massflow_summary_parallel!(
    systems::Vector{Santiago.System},
    M_in::Dict;
    MC,
    n,
    techflows,
    scale_reliability
)

```

Performs Monte Carlo massflow calculations and adds the summary statistics to the to each system *using multi-threading*. Make sure the that you start Julia with multiple threads!

## Arguments:

  * `M_in`: a dictionary containing for each source the inflows of each substance.
  * `MC`: if false, the expected values of the Dirichlet distribution is used as transfer  coefficients. Else, the transfer coefficients are sampled from a Dirichlet distribution.

## Keyword arguments

  * `n`: number of Monte Carlo simulations. Ignored if `MC=false`.
  * `techflows`: if true, the flows of the individual techs are summarized.
  * `scale_reliability`: factor to scale the `transC_reliability` of all `Techs`.
  * `rng`: optional, a random generator. This is only needed for multi-threading to obtain thread-safety.
