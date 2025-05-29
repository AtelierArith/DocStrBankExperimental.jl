Common random variates, also called common random numbers (CRN), are a technique for reducing variance when repeating runs of simulations with different parameters. The idea is to record the randomness of one simulation and replay the same choices in subsequent runs. This particular implementation does this by saving the state of the random number generator every time it's used by a sampler.

The Xoshiro sampler has a relatively small state (32 bytes), which is saved every time the sampler uses random numbers. This CRN recorder saves data in memory, but we could save that to a memory-mapped file so that the operating system will optimize transfer of that memory to disk.

What happens when replays of simulation runs use more draws than the first, recorded simulation? Those simulations draw from a fresh random number generator. This is not an exact approach.

# Example

The goal is to run the simulation with ten different parameter sets and measure how much different parameters change the mean of some quantity determined by the trajectories.

```julia
using Random: Xoshiro
using CompetingClocks
example_clock = (3, 7)  # We will use clock IDs that are a tuple of 2 integers.
sampler = FirstToFire{typeof(example_clock)}()
crn_sampler = CommonRandomRecorder(sampler, typeof(example_clock), Xoshiro)
for trial_idx in 1:100
    run_simulation(model, crn_sampler)
    reset!(crn_sampler)
end
for param_idx in 1:10
    each_model = modify_model!(model, param_idx)
    run_simulation(each_model, crn_sampler)
    reset!(crn_sampler)
end
```
