```
state = initialize_particle_filter(model::GenerativeFunction, model_args::Tuple,
    observations::ChoiceMap, proposal::GenerativeFunction, proposal_args::Tuple,
    num_particles::Int)
```

Initialize the state of a particle filter using a custom proposal for the initial latent state.
