```
xnew = predict(model::AbstractModel, t::Trajectory [, i])
xnew = predict(model::AbstractModel, x, u [, i])
```

現在の状態とアクションを考慮して次の状態を予測します。
