```
(log_incremental_weights,) = particle_filter_step!(
    state::ParticleFilterState, new_args::Tuple, argdiffs,
    observations::ChoiceMap, proposal::GenerativeFunction, proposal_args::Tuple)
```

Perform a particle filter update, where the model arguments are adjusted, new observations are added, and some combination of a custom proposal and the model's internal proposal is used for proposing new latent state.  That is, for each particle,

  * The proposal function `proposal` is evaluated with arguments `Tuple(t_old, proposal_args...)` (where `t_old` is the old model trace), and produces its own trace (call it `proposal_trace`); and
  * The old model trace is replaced by a new model trace (call it `t_new`).

The choicemap of `t_new` satisfies the following conditions:

1. `get_choices(t_old)` is a subset of `get_choices(t_new)`;
2. `observations` is a subset of `get_choices(t_new)`;
3. `get_choices(proposal_trace)` is a subset of `get_choices(t_new)`.

Here, when we say one choicemap `a` is a "subset" of another choicemap `b`, we mean that all keys that occur in `a` also occur in `b`, and the values at those addresses are equal.

It is an error if no trace `t_new` satisfying the above conditions exists in the support of the model (with the new arguments). If such a trace exists, then the random choices not determined by the above requirements are sampled using the internal proposal.
