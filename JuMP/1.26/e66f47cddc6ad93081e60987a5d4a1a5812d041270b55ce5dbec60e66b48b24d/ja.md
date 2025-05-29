```
abstract type AbstractConstraint
```

すべての制約タイプのための抽象基本型です。`AbstractConstraint`は、モデルに格納された制約への単なる参照である[`ConstraintRef`](@ref)とは異なり、関数と集合を直接格納します。`AbstractConstraint`はモデルに添付する必要はありません。
