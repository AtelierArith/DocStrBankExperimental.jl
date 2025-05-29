```
(new_trace, accepted) = involutive_mcmc(trace, proposal::GenerativeFunction, proposal_args::Tuple, involution; ..)
```

[`metropolis_hastings`](@ref) の反転形式のエイリアスです。
