```
moi_set(constraint::AbstractConstraint)
```

制約 `constraint` の集合を関数-in-集合形式で `MathOptInterface.AbstractSet` として返します。

```
moi_set(s::AbstractVectorSet, dim::Int)
```

JuMP集合 `s` に対応する次元 `dim` の MOI 集合を返します。
