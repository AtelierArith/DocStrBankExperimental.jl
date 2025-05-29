```
systems!(env::BaseEnv, systems::Dict)
```

Set systems of `env`. Required before reset!.

# Examples

```julia
systems = Dict("sys" => BaseSystem(initial_state=zeros(3)))
env = BaseEnv()
systems!(env, systems)
```
