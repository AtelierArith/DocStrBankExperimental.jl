```
step!(env::BaseEnv, step)
```

`env`の各ステップの遷移動作を設定します。`reset!`の前に必要です。`update!`を含む必要があります。

# 例

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
