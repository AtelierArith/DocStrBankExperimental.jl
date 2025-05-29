```
set!(turtle; to = O(), head = Z(), up = X(), arm = Y())
```

カメの位置と向きを設定します。引数 `to`、`head`、`up` および `arm` は `Vec` 型である必要があり、キーワード引数として渡されるべきです。

## 例

```jldoctest
julia> turtle = Turtle();

julia> using PlantGeomPrimitives

julia> set!(turtle, to = O(), head = Y(), up = Z(), arm = X());
```
