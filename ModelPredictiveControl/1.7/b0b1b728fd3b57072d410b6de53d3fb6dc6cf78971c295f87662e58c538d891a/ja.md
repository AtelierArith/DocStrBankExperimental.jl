```
LinModel(model::NonLinModel; x=model.x0+model.xop, u=model.uop, d=model.dop)
```

[`linearize(model; x, u, d)`](@ref) を呼び出し、結果の線形モデルを返します。
