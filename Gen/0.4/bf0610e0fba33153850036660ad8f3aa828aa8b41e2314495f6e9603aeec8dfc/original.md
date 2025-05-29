```
(log_incremental_weights,) = particle_filter_step!(
    state::ParticleFilterState, new_args::Tuple, argdiffs,
    observations::ChoiceMap)
```

Perform a particle filter update, where the model arguments are adjusted, new observations are added, and the default proposal is used for new latent state.
