```
ConstraintData{C <: AbstractConstraint}
```

制約オブジェクトを[`GDPData`](@ref)に格納し、それらが持つメタデータを保存するための型です。

**フィールド**

  * `constraint::C`: 制約。
  * `name::String`: 命題の名前。
