```
state = initialize_particle_filter(model::GenerativeFunction, model_args::Tuple,
    observations::ChoiceMap, num_particles::Int)
```

Initialize the state of a particle filter, using the default proposal for the initial latent state.
