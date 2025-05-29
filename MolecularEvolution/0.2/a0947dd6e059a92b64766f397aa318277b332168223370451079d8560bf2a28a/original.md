```
metropolis_step(LL::Function, modifier, curr_value)
```

Does a standard metropolis step in an MCMC, i.e. proposes a candidate symmetrically and returns the next state in the chain, decided by the candidate being rejected or not.

# Interface

You need a `MySampler <: Any` to implement

  * `proposal(modifier::MySampler, curr_value)`
  * `log_prior(modifier::MySampler, x)`
  * `apply_decision(modifier::MySampler, accept::Bool)`

`LL` is by default called on `curr_value` and the returned value of `proposal`. Although, it is possible to transform the current value before proposing a new value, and then take the inverse transform to match the argument `LL` expects.

# Extended interface

## Hastings

To allow for asymmetric proposals, you must overload

  * `log_proposal(modifier::MySampler, x, conditioned_on)`

which returns a constant (`0.0` in particular) by default.

## Transformations

To make proposals in a transformed space, you overload

  * `tr(modifier::MySampler, x)`
  * `invtr(modifier::MySampler, x)`

which are identity transformations by default.
