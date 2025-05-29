```
dyn!(env::BaseEnv, dyn)
```

`env`内の各システムのダイナミクスを設定します。`reset!`の前に必要です。`env`のすべてのシステムの`dot`は関数`dyn`に割り当てられるべきです。

# 例

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
