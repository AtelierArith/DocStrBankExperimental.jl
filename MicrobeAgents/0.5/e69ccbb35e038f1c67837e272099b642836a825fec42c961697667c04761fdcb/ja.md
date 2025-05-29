```
microbe_pathfinder_step!(microbe, model)
```

`microbe_step!`と同じですが、動きはパスファインダー（`model.pathfinder`）によって制約されており、アクセスできない空間の領域が定義されています。
