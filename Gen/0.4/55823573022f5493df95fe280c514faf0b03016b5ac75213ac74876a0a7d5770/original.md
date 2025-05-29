```
(new_trace, accepted) = metropolis_hastings(
    trace, selection::Selection;
    check=false, observations=EmptyChoiceMap())
```

Perform a Metropolis-Hastings update that proposes new values for the selected addresses from the internal proposal (often using ancestral sampling), returning the new trace (which is equal to the previous trace if the move was not accepted) and a Bool indicating whether the move was accepted or not.
