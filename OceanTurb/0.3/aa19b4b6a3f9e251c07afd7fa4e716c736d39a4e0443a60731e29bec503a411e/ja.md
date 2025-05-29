```
set_bcs!(model; bcspecs...)
```

モデルの解場の境界条件を設定します。キーワード引数の名前はモデルの解の名前で、その値は (bottom*bc, top*bc) のタプルです。

# 例

julia> set_bcs!(model, c=(FluxBoundaryCondition(-1),                           FluxBoundaryCondition(0))                 )
