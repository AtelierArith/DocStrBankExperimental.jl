```
struct Periodic{I,V} <: AbstractPhysicalConstraint
    ID::I
    value::V
end
```

周期境界条件モデル。

### フィールド

  * 'ID' – 境界ID
  * `value` – この境界を適用するために必要な情報を含むタプル
