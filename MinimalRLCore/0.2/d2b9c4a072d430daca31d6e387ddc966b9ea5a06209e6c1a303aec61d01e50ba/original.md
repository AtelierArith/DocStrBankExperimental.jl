```
Episode(env, agent, maxn, rng)
```

This is a struct for managing the components of an episode iterator. You should only pass a reference to env and agent, while managing the reference seperately.

# Arguments

  * `env::AbstractEnvironment`: The Environment (following RLCore interface)
  * `agent::AbstractAgent`: The Agent (following RLCore interface)
  * `maxn=0`: Max number of steps for the episode.
  * `rng=nothing`: The Random Number Generator for the episode (can either be nothing or an AbstractRNG)
