```
informationmatrix(model::StatisticalModel; expected::Bool = true)
```

モデルの情報行列を返します。デフォルトではフィッシャー情報行列が返されますが、観測情報行列は `expected = false` を指定することで要求できます。
