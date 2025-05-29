```
dyn!(env::BaseEnv, dyn)
```

Set dynamics of each systems in `env`. Required before reset!. `dot` of all systems of `env` should be assigned in function `dyn`.

# Examples

```julia
function set_dyn(env, t)
    sys = env.systems["sys"]
    x = sys.state
    A = Matrix(I, 3, 3)
    sys.dot = -A * x
end
env = BaseEnv()
dyn!(env, set_dyn)
```
