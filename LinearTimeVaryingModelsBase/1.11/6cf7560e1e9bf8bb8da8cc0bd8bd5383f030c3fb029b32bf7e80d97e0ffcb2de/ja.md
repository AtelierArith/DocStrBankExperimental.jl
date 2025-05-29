```
xnew = simulate(model::AbstractModel, t::Trajectory)
xnew = simulate(model::AbstractModel, x0, u)
```

初期状態とアクションを考慮してシステムを時間的に前方にシミュレートします。
