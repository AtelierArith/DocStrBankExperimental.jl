```
(new_trace, accepted) = metropolis_hastings(
    trace, proposal::GenerativeFunction, proposal_args::Tuple;
    check=false, observations=EmptyChoiceMap())
```

Perform a Metropolis-Hastings update that proposes new values for some subset of random choices in the given trace using the given proposal generative function, returning the new trace (which is equal to the previous trace if the move was not accepted) and a Bool indicating whether the move was accepted or not.

The proposal generative function should take as its first argument the current trace of the model, and remaining arguments `proposal_args`. If the proposal modifies addresses that determine the control flow in the model, values must be provided by the proposal for any addresses that are newly sampled by the model.
