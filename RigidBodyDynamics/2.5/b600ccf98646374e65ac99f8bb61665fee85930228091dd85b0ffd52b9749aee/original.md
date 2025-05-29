```julia
rand_configuration!(state)

```

Randomize the configuration vector $q$. The distribution depends on the particular joint types present in the associated `Mechanism`. The resulting $q$ is guaranteed to be on the `Mechanism`'s configuration manifold. Invalidates cache variables.
