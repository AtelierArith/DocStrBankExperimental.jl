```
(new_trace, accepted) = involutive_mcmc(trace, proposal::GenerativeFunction, proposal_args::Tuple, involution; ..)
```

Alias for the involutive form of [`metropolis_hastings`](@ref).
