```
KMarkovUpdater
```

Updater that stores the k most recent observations as the belief.

Example:

```julia
up = KMarkovUpdater(5)
s0 = rand(rng, initialstate(pomdp))
initial_observation = rand(rng, initialobs(pomdp, s0))
initial_obs_vec = fill(initial_observation, 5)
hr = HistoryRecorder(rng=rng, max_steps=100)
hist = simulate(hr, pomdp, policy, up, initial_obs_vec, s0)
```
