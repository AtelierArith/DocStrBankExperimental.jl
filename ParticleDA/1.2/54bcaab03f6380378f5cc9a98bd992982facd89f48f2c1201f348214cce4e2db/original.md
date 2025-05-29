```
simulate_observations_from_model(
    init_model, input_file_path, output_file_path; rng=Random.TaskLocalRNG()
) -> Matrix
```

Simulate observations from the state space model initialised by the `init_model` function with parameters specified by the `model` key in the input YAML file at  `input_file_path` and save the simulated observation and state sequences to a HDF5 file at `output_file_path`. `rng` is a random number generator to use to generate random variates while simulating from the model - a seeded random number generator may be specified to ensure reproducible results.

The input YAML file at `input_file_path` should have a `simulate_observations` key with value a dictionary with keys `seed` and `n_time_step` corresponding to respectively the number of time steps to generate observations for from the model and the seed to use to initialise the state of the random number generator used to simulate the observations.

The simulated observation sequence is returned as a matrix with columns corresponding to the observation vectors at each time step.
