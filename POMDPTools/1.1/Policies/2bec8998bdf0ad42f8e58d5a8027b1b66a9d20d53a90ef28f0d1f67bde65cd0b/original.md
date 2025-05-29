```
RandomPolicy{RNG<:AbstractRNG, P<:Union{POMDP,MDP}, U<:Updater}
```

a generic policy that uses the actions function to create a list of actions and then randomly samples an action from it.

Constructor:

```
`RandomPolicy(problem::Union{POMDP,MDP};
         rng=Random.default_rng(),
         updater=NothingUpdater())`
```

# Fields

  * `rng::RNG` a random number generator
  * `probelm::P` the POMDP or MDP problem
  * `updater::U` a belief updater (default to `NothingUpdater` in the above constructor)
