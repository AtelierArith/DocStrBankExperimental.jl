````
`moment(traj::Trajectory, N::Int; τ=0.01, order::Int=1)`

軌道のモーメントを計算する関数です。

# 引数
- `traj`: 軌道。   
- `N`: サンプル数。
- `τ`: 時間ステップ。
- `order`: モーメントの次数。

# 例
```julia
using DiffusionX
sp = Bm()
traj = sp(10)
moment(traj, 1000; τ=0.01, order=2)
```
````
