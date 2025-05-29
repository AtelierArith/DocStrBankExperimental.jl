```
run_parallel(queue::Vector{Sim})
run_parallel(f::Function, queue::Vector{Sim})
```

Run `Sim` objects in `queue` in parallel and return results as a `DataFrame`.

By default, the `DataFrame` will contain the reward for each simulation and the metadata provided to the sim.

# Arguments

  * `queue`: List of `Sim` objects to be executed
  * `f`: Function to process the results of each simulation

This function should take two arguments, (1) the `Sim` that was executed and (2) the result of the simulation, by default a `SimHistory`. It should return a named tuple that will appear in the dataframe. See Examples below.

## Keyword Arguments

  * `show_progress::Bool`: whether or not to show a progress meter
  * `progress::ProgressMeter.Progress`: determines how the progress meter is displayed

# Examples

```julia
run_parallel(queue) do sim, hist
    return (n_steps=n_steps(hist), reward=discounted_reward(hist))
end
```

will return a dataframe with with the number of steps and the reward in it.
