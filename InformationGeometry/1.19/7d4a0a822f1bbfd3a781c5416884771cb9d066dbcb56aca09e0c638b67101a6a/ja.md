```
ModifyODEmodel(DM::AbstractDataModel, NewObservationFunc::Function) -> ModelMap
```

与えられたODEベースの`DataModel`から新しい観測関数`f(u,t,θ)`を持つ新しい`ModelMap`を構築します。
