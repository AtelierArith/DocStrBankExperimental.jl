````
`Trajectory(sp::StochasticProcess, T::Float64)` 

確率過程の軌跡の型。

# 引数
- `sp`: 確率過程。
- `T`: 軌跡の長さ。

# 例
```julia
using DiffusionX
sp = Bm()
traj = sp(10)
```
````
