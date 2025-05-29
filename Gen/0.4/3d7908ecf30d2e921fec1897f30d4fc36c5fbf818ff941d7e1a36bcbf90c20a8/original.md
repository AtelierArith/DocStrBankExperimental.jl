```
(new_trace, accepted) = mh(trace, selection::Selection; ..)
(new_trace, accepted) = mh(trace, proposal::GenerativeFunction, proposal_args::Tuple; ..)
(new_trace, accepted) = mh(trace, proposal::GenerativeFunction, proposal_args::Tuple, involution; ..)
```

Alias for [`metropolis_hastings`](@ref). Perform a Metropolis-Hastings update on the given trace.
