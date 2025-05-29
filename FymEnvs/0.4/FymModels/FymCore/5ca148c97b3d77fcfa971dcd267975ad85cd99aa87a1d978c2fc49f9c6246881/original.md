```
step!(env::BaseEnv, step)
```

Set transition behaviour of `env` for each step. Required before reset!. It must contain `update!`.

# Examples

```julia
function step(env)
    t = time(env.clock)
    sys = env.systems["sys"]
    x = sys.state
    update!(env)
    next_obs = sys.state
    reward = zeros(1)
    done = time_over(env.clock)
    info = Dict("time" => t, "state" => x)
    return next_obs, reward, done, info
end
env = BaseEnv()
step!(env, step)
```
