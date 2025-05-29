```
or!(turtle; head = Z(), up = X(), arm = Y())
```

カメを新しい方向に向けるために、ローカル参照システムを再定義します。引数 `head`、`up`、および `arm` は `Vec` 型である必要があります。

## 例

```jldoctest
julia> turtle = Turtle();

julia> using PlantGeomPrimitives

julia> or!(turtle, head = Y(), up = Z(), arm = X());
```
